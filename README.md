rackops_rolebook Cookbook
=========================
This "rolebook" is a replacement for a traditional base role. It includes recipes like a role but is structured like a cookbook.

Requirements
------------
- depends "user"
- depends "motd-tail"
- depends "sudo"
- depends "rackspace_iptables"

Attributes
-----------
- `default['rackops_rolebook']['editor']['default']` - sets the default editor for the entire machine via /etc/profile.d. Defaults to `vim`

Recipes
-------
`default.rb` - This recipe includes all the recipes from the required core cookbooks. It will include chef-client recipes if we are *not* running in chef_solo mode. It adds the `rack` user to the sudo group and installs a bunch of handy applications.
`acl.rb` - This recipe will the standard rackspace IPtables allows.

Usage
-----
#### rackops_rolebook::default
e.g.
Just include `rackops_rolebook` in your node's `run_list`:

```json
{
  "name":"my_node",
  "run_list": [
    "recipe[rackops_rolebook]"
  ]
}
```

License and Authors
-------------------
Author: ryan.richard@rackspace.com
Author: matt.thode@rackspace.com

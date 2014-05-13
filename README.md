rackops_rolebook Cookbook
=========================
This "rolebook" is a replacement for a traditional base role. It includes recipes like a role but is structured like a cookbook.

Requirements
------------
- depends "chef-client"
- depends "rackspace_user"
- depends "rackspace_motd"
- depends "rackspace_sudo"
- depends "rackspace_ntp"
- depends "rackspace_iptables"
- depends "rackspace_cloudmonitoring"
- depends "rackspace_openssh"

Attributes
-----------
- `default['rackops_rolebook']['editor']['default']` - sets the default editor for the entire machine via /etc/profile.d. Defaults to `vim`
- `default['rackops_rolebook']['include_acl']` - Whether or not to include the standard Rackspace iptables ACLs for access. Default to `true`
- `default['rackspace_cloudmonitoring']['standard_checks']['enabled'] - Whether or not to include standard cloud monitoring checks. Default to `false`

Recipes
-------
`default.rb` - This recipe includes all the recipes from the required core cookbooks. It will include chef-client recipes if we are *not* running in chef_solo mode. It adds the `rack` user to the sudo group and installs a bunch of handy applications.
`acl.rb` - This recipe will the standard rackspace IPtables allows.
`monitoring_checks.rb` - Sets up Standard CPU, ram, disk (block and filessytem) and network checks.
 - by default it's looking for `node['rackspace"]['cloud_credentials']['api_key']` and `node['rackspace"]['cloud_credentials']['username']` to be populated. This is best left in an environment or data bag

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

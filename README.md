
# Opsgenie Plugin for Steampipe

Use SQL to query infrastructure including servers, networks, facilities and more from Opsgenie.

- **[Get started →](https://hub.steampipe.io/plugins/turbot/jira)**
- Documentation: [Table definitions & examples](https://hub.steampipe.io/plugins/turbot/jira/tables)
- Community: [Join #steampipe on Slack →](https://turbot.com/community/join)
- Get involved: [Issues](https://github.com/turbot/steampipe-plugin-jira/issues)

## Quick start

### Install

Download and install the latest Opsgenie plugin:

```bash
steampipe plugin install opsgenie
```

Configure your [credentials](https://hub.steampipe.io/plugins/turbot/jira#credentials) and [config file](https://hub.steampipe.io/plugins/turbot/jira#configuration).

Configure your account details in `~/.steampipe/config/opsgenie.spc`:

```hcl
  connection "steampipe-plugin-opsgenie" {
    plugin = "opsgenie"


    # username / Email address of agent user who have permission to access the API (required).
    # default Organization
    #url      = "api.opsgenie.com"
    # for EU Organization
    #url      = "api.eu.opsgenie.com"

    # API token for your opsgenie instance (required).
    # See https://docs.opsgenie.com/docs/api-access-management
    #token      = "YOUR_opsgenie_API_KEY"

    # To filter request you can add opsgenie query
    #query= "status: open AND responders: 'My_Team'"
  }
```


Or through environment variables:


```sh
export OPSGENIE_URL=https://your-domain.atlassian.net/
export OPSGENIE_TOKEN=8WqcdT0rvIZpCjtDqReF48B1
```

Run steampipe:

```shell
steampipe query
```

List teams in your Opsgenie account:

```sql
select 
  team_id,
  name,
 description
from 
  opsgenie_teams;
```

```
+--------------------------------------+------------------------------------+--------------------------------------------+
| team_id                              | name                               | description                                |
+--------------------------------------+------------------------------------+--------------------------------------------+
| 8cfdd4da-73e9-4526-be90-02111f2f2f1f | Infra_Team                         | Infrastructure Team                        |
| 555d4f34-46d5-41b6-88bd-12df8z1f7104 | Dev_Team                           | Developper Team                            |
+--------------------------------------+------------------------------------+--------------------------------------------+
```

## Developing

Prerequisites:

- [Steampipe](https://steampipe.io/downloads)
- [Golang](https://golang.org/doc/install)

Clone:

```sh
git clone https://github.com/jplanckeel/steampipe-plugin-opsgenie.git
cd steampipe-plugin-opsgenie
```

Build, which automatically installs the new version to your `~/.steampipe/plugins` directory:

```
make
```

Configure the plugin:

```
cp config/* ~/.steampipe/config
vi ~/.steampipe/config/opsgenie.spc
```

Try it!

```
steampipe query
> .inspect opsgenie
```

Further reading:

- [Writing plugins](https://steampipe.io/docs/develop/writing-plugins)
- [Writing your first table](https://steampipe.io/docs/develop/writing-your-first-table)

## Contributing

Please see the [contribution guidelines](https://github.com/turbot/steampipe/blob/main/CONTRIBUTING.md) and our [code of conduct](https://github.com/turbot/steampipe/blob/main/CODE_OF_CONDUCT.md). All contributions are subject to the [Apache 2.0 open source license](https://github.com/jplanckeel/steampipe-plugin-opsgenie/blob/main/LICENSE).

`help wanted` issues:

- [Steampipe](https://github.com/turbot/steampipe/labels/help%20wanted)
- [Opsgenie Plugin](https://github.com/turbot/steampipe-plugin-opsgneie/labels/help%20wanted)

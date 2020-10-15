# App-Gitlab

## First Time Prerequisites

1. Ensure this hosts' ssh port is not listening on port 22

## running the containers

1. `cp ./config/gitlab.rb.template ./config/gitlab.rb`
2. update the following lines in [gitlab.rb](./config/gitlab.rb)
    * `external_url 'https://example.com' # todo: changeme`
    * `gitlab_rails['gitlab_email_from'] = 'gitlab@example.com' # todo: changeme`
    * `gitlab_rails['incoming_email_email'] = "gitlab@example.com" # todo: changeme`
    * `gitlab_rails['incoming_email_password'] = "changeme" # todo: changeme`
    * `gitlab_rails['incoming_email_host'] = "mail.example.com" # todo: changeme`
    * `  label: 'changme' # todo: changeme`
    * `  host: 'dc.example.com' # todo: changeme`
    * `  bind_dn: 'cn=binduser,dc=domain,dc=com' # todo: changeme`
    * `  password: 'changeme' # todo: changeme`
    * `  base: 'ou=example,dc=domain,dc=com' # todo: changeme`
    * `  user_filter: '(&(objectcategory=person)(|(memberof=cn=gitlab-users,ou=groups,dc=domain,dc=com)(memberof=cn=gitlab-admins,ou=groups,dc=domain,dc=com)))' # todo: changeme`
    * `  group_base: 'ou=gitlab,ou=groups,dc=domain,dc=com' # todo: changeme`
    * `gitlab_rails['smtp_address'] = "mail.example.com" # todo: changeme`
    * `gitlab_rails['smtp_user_name'] = "gitlab@example.com" # todo: changeme`
    * `gitlab_rails['smtp_password'] = "changeme" # todo: changeme`
    * `gitlab_rails['smtp_domain'] = "example.com" # todo: changeme`
3. update the following volumes in [docker-compose.yml](./docker/docker-compose.yml)
    * `../Data/config:/etc/gitlab`
    * `../Config/gitlab.rb:/etc/gitlab/gitlab.rb`
    * `../Data/logs:/var/log/gitlab`
    * `../Data/data:/var/opt/gitlab`
4. run `docker-compose -f ./docker/docker-compose.yml up -d`

## first time setup

1. Visit <http://your-ip>
2. Enter an admin password
3. Log in with the username `root` and the password you just set

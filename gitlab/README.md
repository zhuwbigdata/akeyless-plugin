# GitLab Plugin



# Create auth method using gitlab JWKS
```
akeyless create-auth-method-oauth2 \
--name /devops/gitlab_auth \
--jwks-uri https://gitlab.com/oauth/discovery/keys \
--unique-identifier user_login \
--force-sub-claims \
--profile devopsapi
Auth Method /devops/gitlab_auth successfully created
```

## Create access role
```
akeyless create-role \
--name /devops/gitlab_role \
--profile devopsapi
A new role named /devops/gitlab_role was successfully created
```

## Asscociate access role with access method
```
akeyless assoc-role-am \
--role-name /devops/gitlab_role \
--am-name /devops/gitlab_auth \
--sub-claims user_login=zhuwbigdata \
--profile devopsapi
Association ass-4mc3cuxzqrn8z3f2sndd was successfully created
```

## RBAC on access role
```
akeyless set-role-rule \
--role-name /devops/gitlab_role  \
--path /devops/'*' \
--capability read \
--capability list \
--profile devopsapi
The requested rule was successfully set to the role /devops/gitlab_role 

```
https://github.com/zhuwbigdata/akeyless-plugin.git


akeyless auth --access-id $ACCESS_ID --access-type jwt --jwt "t-886831d9b42faf3fc633fcb117c0689e" --json --jq-expression='.token'
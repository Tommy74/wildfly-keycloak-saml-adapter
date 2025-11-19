# wildfly-keycloak-saml-adapter

Start Keycloak:
```shell
./bin/kc.sh start-dev --http-port 8180 --log-level=DEBUG
```

go to [http://localhost:8180](http://localhost:8180) and create user admin/admin

Configure Realm, Users and Roles:

* create Realm "example_realm" (make sure “Enabled” is “On”)
* create User "user1" and, under the "Credentials" tabs, set password "passwordUser1" (make sure “Temporary” is “Off”)
* create User "super-user1" and, under the "Credentials" tabs, set password "passwordSuperUser1" (make sure “Temporary” is “Off”)
* create Role "super-user" in "Realm roles"
* create Role "user" in "Realm roles"
* add role "user" to user "user1" in tab "Role Mapping" for the user
* add role "super-user" to user "super-user1" in tab "Role Mapping" for the user
* create User "admin" and, under "Credentials" tabs, set password "admin"
* add ALL "Client roles" to admin (e.g. "create-client")

Configure client:

* Client ID:                          wildfly-keycloak-saml-adapter
* Root URL:                           http://localhost:8080
* Home URL:                           http://localhost:8080
* Valid post logout redirect URIs:    http://localhost:8080/secured/*
* Master SAML Processing URL:         http://localhost:8080/secured/saml
* "Sign documents":                   OFF
* Keys -> Client signature required:  OFF

N.B.: Set `SP="wildfly-keycloak-saml-adapter"` in `/subsystem=keycloak-saml/secure-deployment=ROOT.war/SP="wildfly-keycloak-saml-adapter"` otherwise you'll get "client_not_found" "Cannot_match_source_hash" error from Keycloak

Note: find more info in https://github.com/wildfly/wildfly-cekit-modules/blob/main/jboss/container/wildfly/launch/keycloak/2.0/added/keycloak.sh
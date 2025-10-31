# wildfly-keycloak-saml-adapter

Start Keycloak:
```shell
./bin/kc.sh start-dev --http-port 8180 --log-level=DEBUG
```

go to [http://localhost:8080](http://localhost:8080) and create user admin/admin

Configure Realm, User and Role:

* create Realm "example_realm"
* create User "user1" and, under "Credentials" tabs, set password "passwordUser1"
* create Role "admin" in "Realm roles"
* add role "admin" to user "user1" in tab "Role Mapping" for the user
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
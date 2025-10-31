# wildfly-keycloak-saml-adapter

./bin/kc.sh start-dev --http-port 8180 --log-level=DEBUG

Client ID:                          wildfly-keycloak-saml-adapter
Root URL:                           http://localhost:8080
Home URL:                           http://localhost:8080
Valid post logout redirect URIs:    http://localhost:8080/secured/*
Master SAML Processing URL:         http://localhost:8080/secured/saml
"Sign documents":                   OFF
Keys -> Client signature required:  OFF

N.B.: Set `SP="wildfly-keycloak-saml-adapter"` in `/subsystem=keycloak-saml/secure-deployment=ROOT.war/SP="wildfly-keycloak-saml-adapter"` otherwise you'll get "client_not_found" "Cannot_match_source_hash" error from Keycloak
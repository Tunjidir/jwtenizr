# JWTenizr

jwtenizr creates tokens and ready to use microprofile configuration. 

## installation

Download the executable and self-contained [jwtenizr.jar](https://github.com/AdamBien/jwtenizr/releases/latest) and execute:
`java -jar jwtenizr.jar`

## usage

### initial run

`java -jar jwtenizr.jar` creates:

- `jwtenizr-config.json` with public, private key and target folder of `microprofile-config.properties`
- `jwt-token.json`: with [Minimum MP-JWT Required Claims](https://www.eclipse.org/community/eclipse_newsletter/2017/september/article2.php), a sample principal and a few groups
- `token.jwt`: with information loaded from: `jwt-token.json` and can be used as input for automated  system tests
- `microprofile-config.properties` comprising the public key an the issuer: copy to your `WAR/src/main/resources/META-INF` 
- `curl` command: with `Authorization` header and included token:

```curl -i -H'Authorization: Bearer eyJraW¢...(generated JWT token)' http://localhost:8080[RESOURCE and SUB-RESOURCES]```

### customizations

- Adjust the `groups[]` to configure roles and `upn` to change the principal in `jwt-token.json` then re-execute JWTenizr
- Add additional claims by extending: `jwt-token.json`

Note: The iss in `jwt-token.json` has to correspond with the `mp.jwt.verify.issuer` in `microprofile-config.properties`

## run from anywhere

A a shell script:

```shell
#!/bin/bash
BASEDIR=$(dirname $0)
java -jar ${BASEDIR}/jwtenizr.jar "$@"%
```

will install JWTenizr "globally". Now you can launch JWTenizr from any directory you like

## in action

[![](https://i.ytimg.com/vi/twXqCoYQ16c/mqdefault.jpg)](https://www.youtube.com/embed/twXqCoYQ16c?rel=0)

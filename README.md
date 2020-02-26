# ESCAPE AAI documentation

The [ESCAPE IAM instance][escape-iam] is now available.

Registration is active. Users can authenticate via Google, IAM and using their
EduGAIN IdP (if necessary attributes are provided by the IdP). 

IAM documentation is available [here][iam-docs].

Client applications can be registered following these
[instructions][client-registration].

VOMS support is enabled. To link an X.509 certificate to an existing IAM escape
account, follow this [instructions][x509-linking]. As in VOMS, multiple
certificates can be linked to an account.

## ESCAPE VO configuration

- [VOMSES](./voms-config/voms-escape.cloud.cnaf.infn.it.vomses)
- [LSC](./voms-config/voms-escape.cloud.cnaf.infn.it.lsc)

## Presentations

- [ESCAPE AAI presentation (joint WP2/WP5 Workshop, July 2019)][escape-aai-slides-020719]

[escape-iam]: https://iam-escape.cloud.cnaf.infn.it
[iam-docs]: https://indigo-iam.github.io/docs
[client-registration]: https://indigo-iam.github.io/docs/v/current/user-guide/client-registration.html
[x509-linking]: https://indigo-iam.github.io/docs/v/current/user-guide/account-linking/x509.html
[escape-aai-slides-020719]: https://indico.in2p3.fr/event/19214/contributions/73463/attachments/54261/70956/ESCAPE-AAI-020719.pdf

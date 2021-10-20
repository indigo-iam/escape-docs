# ESCAPE AAI documentation

The [ESCAPE IAM instance][escape-iam] is now available.

Registration is active. Users can authenticate via Google, IAM and using their
EduGAIN IdP (if necessary attributes are provided by the IdP). 

IAM documentation is available [here][iam-docs].

Client applications can be registered following these
[instructions][client-registration].

VOMS support is enabled. To link an X.509 certificate to an existing IAM escape
account, follow these [instructions][x509-linking]. As in VOMS, multiple
certificates can be linked to an account.

## ESCAPE VO configuration

- [VOMSES](./voms-config/voms-escape.cloud.cnaf.infn.it.vomses)
- [LSC](./voms-config/voms-escape.cloud.cnaf.infn.it.lsc)

To have a working VOMS configuration for the ESCAPE VO:

- place the lsc file in the `/etc/grid-security/vomsdir/escape` directory
- place the vomses file in the `/etc/vomses` directory (only needed if you need to do voms-proxy-init)

The latest supported VOMS clients are required (i.e., voms-proxy-init v. >=3 ).
Also note that this VO is supported by IAM, i.e. there are no VOMS Admin
endpoints that can be used to generate Gridmap files.

## Token based AuthN/Z

Token-based authorization in the ESCAPE data lake will be realized extending
the work done in the context of the [WLCG Authorization Working group][wlcg-authz-wg],
in particular on the [WLCG JWT profile][wlcg-jwt-profile].

We will work in incremental steps towards support for group-based fine-grained
authorization, according to the requirements defined in the [ESCAPE namespace
authorization proposal][namespace-authz-proposal].

### Step 0: coarse-grained VOMS and token-based authorization

The objective of this first step is to enable coarse-grained access to the
ESCAPE namespace to the ESCAPE VO members.

The authentication and authorization requirements are:

- members of the `/escape` group have read/write/delete access to the `/escape`
  namespace
- access to anonymous users is forbidden

These requirements will be honoured for VOMS and token-based authz.

A [testsuite][escape-auth-tests] has been developed to assess compliance of the
ESCAPE datalake with the requirements above.

### Token request instructions

In order to support token-based authn/z as described above, tokens should be
requested to include, at least, the following scopes:

- `openid`
- `wlcg.groups`

With `oidc-agent` this would be done with a command like:

```
> oidc-token -s openid -s wlcg.groups escape
```

For more information on how to use oidc-agent to get tokens out of IAM, see the
[relevant IAM documentation][getting-token-docs].


## Presentations

- [ESCAPE AAI Webinar (April 2020)][escape-aai-webinar]
- [ESCAPE AAI presentation (joint WP2/WP5 Workshop, July 2019)][escape-aai-slides-020719]

[wlcg-authz-wg]: https://twiki.cern.ch/twiki/bin/view/LCG/WLCGAuthorizationWG
[wlcg-jwt-profile]: https://zenodo.org/record/3460258
[escape-iam]: https://iam-escape.cloud.cnaf.infn.it
[iam-docs]: https://indigo-iam.github.io
[client-registration]: https://indigo-iam.github.io/docs/v/current/user-guide/client-registration.html
[x509-linking]: https://indigo-iam.github.io/docs/v/current/user-guide/account-linking/x509.html
[escape-aai-slides-020719]: https://indico.in2p3.fr/event/19214/contributions/73463/attachments/54261/70956/ESCAPE-AAI-020719.pdf
[escape-aai-webinar]: https://indico.in2p3.fr/event/21072/
[escape-auth-tests]: https://github.com/indigo-iam/escape-auth-tests
[namespace-authz-proposal]: https://docs.google.com/document/d/1bWGVH1GlIWy-KMMl9ubqIdvyjGJbNf6W_JwpQ2DhV90/edit
[getting-token-docs]: https://indigo-iam.github.io/v/current/docs/tasks/user/getting-a-token/#obtaining-a-token-using-oidc-agent

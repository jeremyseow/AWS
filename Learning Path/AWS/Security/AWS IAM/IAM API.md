- `AssumeRole`
Returns a set of temporary security credentials that you can use to access AWS resources that you might not normally have access to. Typically, you use AssumeRole within your account or for cross-account access.
- `AssumeRoleWithSAML`
The AssumeRoleWithSAML API operation returns a set of temporary security credentials for federated users who are authenticated by your organization's existing identity system
- `AssumeRoleWithWebIdentity`
The AssumeRoleWithWebIdentity API operation returns a set of temporary security credentials for federated users who are authenticated through a public identity provider e.g. Amazon, FB, Google, any OIDC provider
- `GetFederationToken`
The GetFederationToken API operation returns a set of temporary security credentials for federated users. This API differs from AssumeRole in that the default expiration period is substantially longer (12 hours instead of one hour)

Requires an IAM user or root. The resulting permissions inherit the permissions of the caller, scoped down by the permissions attached in the request (if you don’t attach permissions, the resulting permissions will be deny). The actual permissions associated with the session are the intersection of the caller’s base permissions and the permissions attached as an API parameter
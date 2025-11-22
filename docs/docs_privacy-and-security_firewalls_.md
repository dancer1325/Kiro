# Configuring a firewall, proxy server, or data perimeter for Kiro - IDE - Docs - Kiro

Source: https://kiro.dev/docs/privacy-and-security/firewalls/

---

If you're using a firewall, proxy server, or data perimeter, make sure to allowlist traffic to the following URLs and Amazon Resource Names (ARNs) so that Kiro works as expected.
General urls to allowlist
In the following URLs, replace:
idc-directory-id-or-alias with your IAM Identity Center instance's directory ID or alias. For more information about IAM Identity Center, see What is IAM Identity Center? in the AWS IAM Identity Center User Guide.
sso-region with the AWS Region where your IAM Identity Center instance is enabled.
URLPurpose<idc-directory-id-or-alias>.awsapps.comAuthenticationoidc.<sso-region>.amazonaws.comAuthentication*.sso.<sso-region>.amazonaws.comAuthentication*.sso-portal.<sso-region>.amazonaws.comAuthentication*.aws.devAuthentication*.awsstatic.comAuthentication*.console.aws.a2z.comAuthentication*.sso.amazonaws.comAuthenticationhttps://aws-toolkit-language-servers.amazonaws.com/*Kiro, language processinghttps://aws-language-servers.us-east-1.amazonaws.com/*Kiro, language processinghttps://client-telemetry.us-east-1.amazonaws.comKiro, telemetrycognito-identity.us-east-1.amazonaws.comKiro, telemetryPage updated: November 16, 2025Infrastructure securityVPC endpoints (AWS PrivateLink)
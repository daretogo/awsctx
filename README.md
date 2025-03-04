## SSO VARIANT

This is a fork of the [awsctx](https://github.com/gmolau/awsctx) provided by gmolau, but instead of setting secret access keys it sets sso_session, sso_account_id, sso_role_name, and region. 


# awsctx

Like [kubectx](https://github.com/ahmetb/kubectx), but for AWS profiles. Prompts you to select one of your configured AWS profiles, then sets the default AWS CLI config values based on this profile.

Depends on the AWS CLI and fzf. Works purely through the AWS CLI config mechanism, does not do anything fancy for itself.

## Installation

Ensure you have `fzf` installed.  Easy enough to just `brew install fzf` if you don't. 

Simply put the `awsctx` script somewhere in your $PATH, e.g.

```bash
curl -o /usr/local/bin/awsctx https://raw.githubusercontent.com/daretogo/awsctx/main/awsctx
chmod +x /usr/local/bin/awsctx
```

## FAQ

### How can I display the activated profile in my [Starship](https://starship.rs) prompt?

The default AWS module in Starship reads the `AWS_PROFILE` environment variable, which this script does not set. However, you can use a custom module in combination with the `awsctx --current` command to replicate the same behavior. For this you need to add something like this to your `starship.toml`:

```toml
[custom.awsctx]
command = "awsctx --current"
style = "bold yellow"
format = "[($output)]($style)"
when = true
```

For modifying the order of modules in the prompt see the [Starship docs](https://starship.rs/config/#prompt).

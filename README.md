# default-browser

> [!NOTE]
> I forked this repo in hopes of addressing a problem with default-browser v1.0.18: It fails to work when the user’s home directory has been relocated outside the startup volume. See Issue #23 [“default-browser assumes home directory is /Users/<username>, which fails for relocated macOS home directories #23](https://github.com/macadmins/default-browser/issues/23)”
>
> Commit 9768a2bd82a0c9f71e3c4525a6008f0d7d2b3b4d reflects an untested modification to pkg/client/client.go that hopefully fixes this problem.

This is a tool that will set the default browser for the current user on a macOS device.

## Usage

```shell
/opt/macadmins/bin/default-browser --identifier com.google.chrome
```

To set other browsers as the default, use the following identifiers:

- Google Chrome (the default if no identifier is passed): `com.google.chrome`
- Safari: `com.apple.safari`
- Firefox: `org.mozilla.firefox`
- MS Edge: `com.microsoft.edgemac`

## Known issues

### System Settings may not work correctly

If System Settings doesn't show all sections correctly after running, this tool, restart the machine. This is likely a timing issue with Launch Services, but we haven't reproduced it consistently. If you see that a restart doesn't fix the issue, you way wish to use the `---no-rebuild-launchservices` flag. This will mean that you need to reboot after running the tool.

![System Settings screenshot](assets/system_settings.png)

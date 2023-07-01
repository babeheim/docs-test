## Supported Package managers

Font Awesome supports the following package managers:

- [npm](https://www.npmjs.com/)
- [classic yarn](https://classic.yarnpkg.com/lang/en/) (1.x)
- [modern yarn](https://yarnpkg.com/) (2.x+)

## Private and Public npm Repositories

|Repository|Public|Require active Pro subscription|Font Awesome Pro|Font Awesome Free|
|:-|:-:|:-:|:-:|:-:|
|`https://npm.fontawesome.com` | :x: | :white_check_mark: | :white_check_mark: | :white_check_mark:
|`https://registry.yarnpkg.com` | :white_check_mark: | :x: | :x: | :white_check_mark:
|`https:/registry.npmjs.org` | :white_check_mark: | :x: | :x: | :white_check_mark:

**Note:** To use the private npm repo, an active subscription to Font Awesome Pro is required.

## Configuration Troubleshooting Commands

Use the following commands to get configuration information for your package manager:

- npm: `npm config list`
- classic yarn: `yarn config list --verbose`
- modern yarn: `yarn config --why` (pay attention to `npmScopes` entry)

### Use the Private Repository

If your application needs to use the private repository, ensure that credentials are set:

#### `npm` example output
```
; "user" config from /path/to/.npmrc
# ...
@fortawesome:registry = "https://npm.fontawesome.com/" 
//npm.fontawesome.com/:_authToken = (protected) 
```

#### classic `yarn` example output
```
verbose 0.100133333 Found configuration file "/path/to/.npmrc".
# ...
'@fortawesome:registry': 'https://npm.fontawesome.com/',
'//npm.fontawesome.com/:_authToken': FONT-AWESOME-PACKAGE-FONT-AWESOME-PACKAGE-TOKEN,
```

#### modern `yarn` example output
```
➤ YN0000: npmScopes                     undefined, /path/to/.yarnrc.yml   Map(1) { 'fortawesome' => Map(6) { 'npmAlwaysAuth' => true, 'npmAuthIdent' => null, 'npmAuthToken' => '********', 'npmAuditRegistry' => null, 'npmPublishRegistry' => null, 'npmRegistryServer' => 'https://npm.fontawesome.com/' } }
# ...
```

#### Token in environment variable

It is recommended to store the token in an environment variable in order to avoid to commit it in a public repository.

Make sure that the environment variable is available and readable by the package manager, this may be the cause of
authentication issues on remote servers.

### Use the Public Repository

If your application needs to use the Public Repository, ensure that the above configuration is not set.

## Switching from Private to Public Repository (and vice versa)

When switching from the Private Repository to the Public Repository, remove the currently installed Font Awesome packages from the lock file. The specific command to do this depends on the package manager you are using (`yarn` or `npm`).

## Per-Project npm Configuration

It is recommended to use [per-project npm configuration](https://fontawesome.com/v6/docs/web/setup/packages#set-up-npm-token-for-a-specific-project).

If a global configuration is provided for Font Awesome Pro, it is possible to use per-project configuration for projects that require Font Awesome Free, so that the lock files are not overwritten with references to the Private npm Repository.

```
# per-project configuration example for `yarn` to force the usage of the Public Repository
@fortawesome:registry=https://registry.yarnpkg.com
```

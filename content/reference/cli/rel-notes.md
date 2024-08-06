---
title: "Release Notes"
metaTitle: "Upbound CLI - Release Notes"
description: "Release Notes for the up CLI"
weight: 200
---

Find below the release notes for all released versions of the [up CLI]({{< ref "reference/cli/_index.md" >}}).

<!-- vale off -->

## v0.32.0

Released August 2nd, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.32.0)

### What's Changed

- New `up team` command for managing teams.
- New `up robot team` command for managing robot team membership.
- New `up repository permission` command for managing team access to repositories.
- `up space attach` and `up space detach` have been renamed to `up space connect` and `up space disconnect`, respectively.
- Improved `up alpha get` and `up alpha query` commands for querying resources in and across control planes.


## v0.31.0

Released June 7th, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.31.0)

{{< hint "important" >}}
- Web-based login (previously `up alpha web-login`) is now the default for `up login`. Use `up login --username=<user>` to invoke interactive terminal login.
- `up configuration` is now stubbed out, since Configurations are not currently supported in Upbound.
{{< /hint >}}

### What's Changed

- Web login is now the default for `up login`.
- `up ctx` now works with connected Spaces.
- `up ctx` now supports navigating between cloud, connected, and disconnected Spaces regardless of the current kubeconfig context.
- `up space attach` now works with Upbound IAM.

## v0.30.0

Released May 10th, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.30.0)

### What's Changed

- We promoted `up web-login` to stable.
- We fixed several bugs related to `up ctx` failing to connect to a Space, group, or managed control plane.
- `up version` now prints information seperated into client (your up CLI version) and server (version information for the managed control plane and Space you're connected to)
- `up space init` enables hub authz and authn by default.

## v0.29.0

Released May 3rd, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.29.0)

{{< hint "important" >}}
This release contains an important breaking change that affects how users gain access to the API server of their managed control planes.

For users who've deployed MCPs to Upbound prior to April 30th, 2024 (on our 'legacy GCP Space'), to connect to those MCPs you **must** use `up` ver <= `v0.28.0`.

To connect to an MCP in a Cloud Space or Connected/Disconnected Space, please use `up` ver >= `v0.29.0`.
{{< /hint >}}

### Notable Changes

- We replaced `up ctp connect/disconnect` and `up ctp kubeconfig get` with a new `up ctx` command.
- We've overhauled how profiles work in `up`. Learn more about it by reading the [up CLI]({{<ref "reference/cli">}}) reference.

### What's Changed

- We introduced `up space list` to list all Cloud and Connected Spaces that exist in an organization's account.
- We added CRUD support for control plane groups with `up group` subcommand.
- We bumped the prerequisite version of UXP to `v1.15` when using `up space init` to create a single-tenant Space.
- We fixed some bugs that caused `up space detach` to fail.
- `up ctp list` now derives its context according to what's been set with `up ctx`.
- `up space init` now installs opentelemetry-operator as a prerequisite.
- All commands in `up` now use the new `up` profiles and kubecontexts.

## v0.28.0

Released April 2nd, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.28.0)

### What's Changed

- We added `up alpha space attach` and `detach` commands to facilitate connecting a single-tenant Space to Upbound's global console.

## v0.27.0

Released March 27th, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.27.0)

### What's Changed

- We fixed a bug that caused `up ctp connect` to fail to connect to a managed control plane running in a single-tenant Space.
- We fixed a bug impacting `up xpkg build` against Docker 1.25

## v0.26.0

Released March 16th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.26.0)

### What's Changed

- We added`up alpha query` and `up alpha get` commands.
- We changed `up trace`'s arguments to align with `up query` and `up get` and fixed up/down navigation.

## v0.25.0

Released March 12th, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.25.0)

### Notable Changes

- We updated `up version` to print client and server side versions.
- We improved the UX of `up ctp connect/disconnect`. Connect now gracefully handles different context names and allows repeated connect attempts.

### What's Changed

- We fixed an issue in `up migration` that restored package statuses.
- `up migration` now uses the same confirmation dialog as `up space init`
- We improved the UX of `up ctp connect/disconnect`. Connect now gracefully handles different context names and allows repeated connect attempts.
- We unified the experience between `up ctp connect` and `up ctp kubeconfig get`.
- We added `alpha trace` and `alpha tview` template commands.
- We updated `up version` to print client and server side versions.

## v0.24.2

Released February 29th, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.24.2)

### What's Changed

- This version includes some configuration tweaks for Crossplane and providers that is installed as prerequisites with the up space init command.

## v0.24.1

Released February 7th, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.24.1)

### What's Changed

- We fixed an issue in `up migration` that restored package statuses.
- `up migration` now uses the same confirmation dialog as `up space init`

## v0.24.0

Released February 1st, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.24.0)

### What's Changed

- We introduced `up alpha web-login`, a preview feature to allow web-based authentication to Upbound from `up`.

## v0.23.0

Released February 1st, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.23.0)

### What's Changed

- Updated component prerequisite versions for an Upbound Space.
- We fixed an issue where `up migration` didn't wait for PackageRevisions to be healthy in order to complete a successful migration.
- Space subcommands now respect control plane groups.

## v0.22.1

Released January 30th, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.22.1)

### What's Changed

- Updated component prerequisite versions for an Upbound Space.

## v0.22.0

Released January 30th, 2024.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.22.0)

### Notable Changes

- New `up alpha migration` commands to export state from a control plane and import it into an Upbound managed control plane.
- Allow creation of managed control planes without being configured to use Upbound's deployment service.

### What's Changed

- Improved the help text to make `up profile set space` more discoverable.
- Allow creating new Upbound profiles with `type: space` by name.
- Fixed an issue where `up space init` ignored SIGINT.

## v0.21.0

Released October 12th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.21.0)

### Notable Changes

- `up space init`'s UXP auto-installed prerequisite was updated from 1.12.2-up.2 to 1.13.2-up.2
- `up ctp connect` was re-introduced, with different functionality. Invoking the command will now connect your kubectl directly to the target control plane. Any kubectl commands run in that terminal will be executed against the target control plane.
- `up ctp disconnect` was introduced to compliment connect. Invoking the command will switch from the control plane context back to the originating context.
- `up ctp connector install` was extended to enable configuring mcp-connector against a Space's control plane.
- `up ctp connector uninstall` was introduced to compliment install. Invoking the command will delete the mcp-connector helm chart from the App Cluster.

### What's Changed

- Re-introduce `up ctp connect` add `up ctp disconnect`
- Bump the UXP prereq for spaces to v1.13.2-up.2
- MCP Connector support for Spaces

## v0.20.0

Released October 10th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.20.0)

### Notable Changes

- Introduced support for the following `up ctp` subcommands with spaces:
  - `create`
  - `delete`
  - `get`
  - `list`
- ⚠️ Breaking change ⚠️ `up ctp connect` was moved to up `ctp connector install`. This is anticipation of future work.

### What's Changed

- Add tests for auth.yaml inclusion in provider package
- Allow pre-release versions of spaces to be installed and upgraded to
- Introduce support for up ctp (create, get, list, delete) against an Upbound Space
- Move ctp connect to ctp connector install

## v0.19.2

Released October 5th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.19.2)

### What's Changed

- Fix `up xpkg build` not including authentication extensions for Upbound console on Provider v1

## v0.19.1

Released August 29th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.19.1)

### What's Changed

- [Backport release-0.19] Fix `uxp install` error "couldn't find binding"

## v0.19.0

Released August 28th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.19.0)

### Notable Changes

- New subcommands to support Upbound Spaces
- Add `up space billing get` with GCS support

### What's Changed

- Add repeatable --debug (short -d) enabling API request logging
- Package composition function types
- Prevent deferred File.Close and wrap errors while putting CRDs into xpls provider package cache
- [DevEx] xpkg: add error contexts and print & fail on parse errors
- Add `up space billing get` with GCS support
- Add AWS support to `up spaces billing get`
- New subcommands to support Upbound Spaces
- Introduce additional requirements for the spaces install
- Adjust ingress-nginx deployment to target kind
- Spaces: add helpers for default and unattended installation
- Allow operators to override the registry and registry-endpoint for a spaces install
- Spaces: add support for public load balancer
- Add Azure support to `up space billing get` + provider-generic refactor
- cmd space: fix missing install.Context
- Space: improve destroy command
- space: unify and deduplicate registry flag logic
- Use concrete types with destroyCmd.Run()
- Fix typo in up space destroy output
- Rename `up space billing get` to export and fix event tags

## v0.18.0

Released June 27th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.18.0)

### What's Changed

- Make `help` more accessible
- Updates dependencies to get up close to current

## v0.17.0

Released May 12th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.17.0)

### What's Changed

- Added tab completion for two control plane commands
- Check the validity of kubeconfig before applying it
- xpkg batch subcommand to batch process provider packages

## v0.16.1

Released April 17th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.16.1)

### Notable Changes

- This patch release for `v0.16.0` notably adds a contribution guide and fixes a marshaling bug when building bundled provider packages (if no controller image ref is passed).

### What's Changed

- add contribution guide that includes release process.
- Reorganize organization user commands.

## v0.16.1

Released April 17th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.16.1)

### Notable Changes

- This patch release for `v0.16.0` notably adds a contribution guide and fixes a marshaling bug when building bundled provider packages (if no controller image ref is passed).
- ⚠️ Breaking change ⚠️ With the core crossplane dependency bumped to `v1.6.0` , only `v1` API versions will be supported for `Composition` and `CompositeResourceDefinition` in the `apiextensions.crossplane.io` group. Support for `v1beta1` versions was removed. Please plan to update to `v1` and see the README for more details.

### What's Changed

- add contribution guide that includes release process.
- Reorganize organization user commands.

## v0.16.0

Released March 28th, 2023.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.16.0)

### Notable Changes

- Introduction of many new commands to coincide with the relaunch of [Upbound](https://console.upbound.io), including many commands in `ctp` and `cfg`.
- ⚠️ Breaking change ⚠️ Starting in v0.16.0, `up controlplane create` must supply a required flag `--configuration-name` and no longer supports creating "empty canvas" control planes. Prior versions of up that do not have this flag will now get an error response from the Upbound API:`{"message":"configurationId is required"}`

### What's Changed

- Add `ctp get` command, to show a single control plane.
- Added get commands for orgs, repos, robots, and robot tokens
- Implement JSON and YAML output formatting
- Add formatted ouput for more get & list commands
- Add alpha commands for MCP connector
- update up-sdk-go to use new error descriptions
- Initial suport for tab completions
- Introduce `configuration` commands
- Add completion predictors for control planes, profiles, repos, and robots
- Add completion predictor for configurations
- Add first iteration of `configuration create`
- Update login to fetch default user account if none specified
- Require configurations for creating control planes
- Separate kubeconfig generation steps
- Update gitsources login to pass port parameter.
- Add Organization user management
- Add support for listing configuration templates
- Disable the `upbound` subcommand.
- Revised the new "org user" comands to take an org name instead of an org ID
- Move `controlplane` commands to stable maturity level
- Create a token as part of connect command
- docs: add controlplane commands
- connect: fix the robot creation call
- Querying control planes with no associated configurations
- Update docs: add configuration, remove 'upbound'.
- Added --private flag for `up cfg create`
- connect: always create user token if not provided - no creation of robots
- connect: wait for helm installation to complete
- combine xpkg auth ext anno during build
- Move up ctp kubeconfig get to stable

## v0.15.0

Released November 6th, 2022.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.15.0)

### What's Changed

- Support webhook configurations in provider packages

## v0.14.0

Released October 5th, 2022.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.14.0)

### Notable Changes

- Two new commands, `up ctp provider install` and `up ctp configuration install`, to quickly install Providers and Configurations into any control plane.
- The promotion of the experimental managed control planes (MCP) API to be the default for all `up alpha ctp` commands.
- ⚠️ Breaking change ⚠️ The promotion of the experimental MCP API may break some workflows, but all impacted commands fall under the `alpha` maturity group. Guarantees around backwards compatibility are explained in detail in the [API Maturity](https://github.com/upbound/up/blob/main/docs/maturity.md) documentation. While breaking changes will try to be minimized from version to version, `up` is not guaranteed to maintain backwards compatibility for pre-v1.0 versions.

### What's Changed

- Use compact usage output
- Drop `UP_MCP_EXPERIMENTAL` in favor of new control planes API
- Add support for `up ctp provider install` and `up ctp configuration install`
- Move control plane commands to only support previously experimental API
- Clean up remaining mcp ID references in docs

## v0.13.0

Released August 26th, 2022.
[Release reference on GitHub](https://github.com/upbound/up/releases/tag/v0.13.0)

### Notable Changes

- drastically increases the functionality of up by introducing command groups for `organization`, `robot`, `repository`, and `profile`.
- restructures the up command graph by adding top-level "maturity" groups. Commands that are expected to change or evolve in the future are now nested under `up alpha`. See the [API Maturity](https://github.com/upbound/up/blob/main/docs/maturity.md) documentation for more information.

### What's Changed

- Do not prompt for username / password if token is provided
- Only pass domain to docker-credential-up
- Embed Kubernetes client auth plugins
- Update comment about auth plugins
- Drop up uxp connect command
- Update MCP experimental ctp list with paging
- Move to pterm, emit success message for all operations, and support `--quiet` and `--pretty` global output config
- Add support for repository management and create on push
- Add Nix installation instructions
- Simplify `up upbound install` and add config command group
- Add support for organization management commands
- Support robot management commands
- Add `--force` option to destructive commands
- Move experimental and preview commands to `alpha` group
- Fix up logout and hint when session is missing
- Add support for `up ctp pull-secret create` and require token create output
- Cleanup command structure and allow creating new named profile on login
- Fix top-level alpha command help output and updates docs for v0.13.0 release
- Update configuration docs to include base config

## v0.12.2 and earlier

Consult the [GitHub releases page](https://github.com/upbound/up/releases) for earlier version of the up CLI and its changelog.

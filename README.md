# evas-agent

Based on the [eve Coding Agent template](https://eve.dev/templates/eve-coding-agent-template).

The selected channels are configured through Vercel Connect. Mention @evas-agent in a GitHub issue or pull request comment after deployment. Set GITHUB_BOT_NAME to your GitHub App slug if it differs from the project name. GitHub invocations require repository owner, member, or collaborator standing.

The code extension provides investigation, review, and read-only worker skills. Edits use code__apply_patch.

Authenticated git__gh commands require a signed-in caller and use a user access token from the selected GitHub App through Vercel Connect. GitHub limits that token to the intersection of the caller's access and the App's repository access and permissions; Firecracker-svg is the selected GitHub App owner. Turns started from a GitHub comment cannot run git__gh: they work from the checked-out repository and reply in the thread, so content under review cannot use the commenter's access elsewhere. Public source may also be readable without authentication. Channel replies and the initial repository checkout use an App installation token, not the caller's token. Keep the reset-github-egress hook to clear the installation token's network access before the model runs; it does not remove source already checked out. GITHUB_CONNECTOR defaults to github/evas-agent-github.

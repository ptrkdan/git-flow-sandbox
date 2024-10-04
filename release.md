# Release Flow

1. Ensure all features and fixes have been merged into the `main` branch.

2. Run the "[Bump Version](.github/workflows/bump-version.yml)" workflow and select the appropriate version bump. This will create a branch, `release/<new-version-number>` and a PR that will update the current version written in `package.json`.

3. Approve and merge the release PR into `main`. This will trigger the "[Draft Pre-Release](.github/workflows/draft-pre-release.yml)" workflow, and draft a new release that is set as a "pre-release".

4. Open the release draft, and publish.

> [!IMPORTANT] 
> For staging release, ensure that "Set as a pre-release" is checked!

5. This will trigger the "[Deploy to Staging](.github/workflows/deploy-to-staging.yml)" workflow and create an action, awaiting for approval.

6. Approve the action to deploy to staging.

7. Verify staging deployment.

8. For production deployment, uncheck "Set as a pre-release", check "Set as the latest release", and update the release. This will trigger the "[Deploy to Production](.github/workflows/deploy-to-production.yml)" workflow and create an action, awaiting for approval.

9. Approve the action to deploy to production.

 


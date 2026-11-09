# Branch workflow

- `main`: stable production branch; configure as the Vercel Production Branch.
- `develop`: integration branch; use Vercel Preview deployments for testing.
- `feature/<name>`, `fix/<name>`, `chore/<name>`: short-lived branches created from `develop`.

## Changes

1. Create a working branch from the latest `develop`.
2. Open a pull request targeting `develop`.
3. Run `npm ci`, `npm run lint`, and `npm run build`; check the Vercel preview.
4. Squash merge the pull request and delete the working branch.
5. Release through a pull request from `develop` to `main`. Use a merge commit to preserve shared history between these long-lived branches.

For an urgent production fix, branch from `main`, open a pull request to `main`, then merge `main` back into `develop`.

## Branch protection

The workflow above is a convention until GitHub branch protection is available.
GitHub currently rejects both rulesets and classic branch protection for this private repository with HTTP 403 and requests a plan upgrade.

When available, protect both `main` and `develop`: require pull requests, block force pushes and branch deletion, and require CI checks once configured. Keep `main` as the default branch.

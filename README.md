# augur-fleet

The AUGUR deployments Harry runs, declared as files for `augurctl` (in the `augur` repository,
`scripts/augurctl/`). Private: it names real servers.

- `deployments/<name>.yaml`: one server each, held to augur's `scripts/augurctl/deployment.schema.json`.
- `secrets/<name>.sops.env`: that server's secrets, encrypted with sops for the age keys in `.sops.yaml`.
  Never commit one unencrypted.
- `catalog/deployments.yaml`: the same servers as Backstage entities, for the company portal (backstage-hb reads it).
  Keep each one's ring and URL as its deployment file says.

From a checkout of augur:

    node scripts/augurctl/augurctl.mjs check --dir <this repo>/deployments
    node scripts/augurctl/augurctl.mjs plan workbench --dir <this repo>/deployments

No CI runs here.

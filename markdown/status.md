What's in a PG's
# status?


### `active+clean`
Normal state

PG processes requests

Correct number of replicas available


### `degraded`
Fewer than pool `size` replicas available


### `recovering`
Catching up from `degraded` state


### `backfill`
Like `recovering`, but starting with empty replica


### `incomplete`
Fewer than pool `min_size` replicas available

Need another OSD, or CRUSH map change, or change to `min_size`


### `inconsistent`
`scrub` or `deep-scrub` detected errors

`ceph pg repair` required


### `down`

Critical data missing, PG unavailable

Need OSD back (or must be declared `lost`)

Check `down_osds_we_would_probe` in `pg query`
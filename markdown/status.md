What's in a PG's
# status?


### `active+clean`
Normal state

PG processes requests

Correct number of replicas available


### `degraded`
Fewer than pool `size` replicas available

<!-- .element class="fragment" -->No action needed, recovery commences when `mon_osd_down_out_interval` expires


### `recovering`
Catching up from `degraded` state


### `backfill`
Like `recovering`, but starting with empty replica


### `incomplete`
Fewer than pool `min_size` replicas available

<!-- .element class="fragment" -->Need another OSD, or CRUSH map change, or change to `min_size`


### `inconsistent`
`scrub` or `deep-scrub` detected errors

<!-- .element class="fragment" --> `ceph pg repair` required


### `down`

Critical data missing, PG unavailable

<!-- .element class="fragment" --> Need OSD back (or must be declared `lost`)

<!-- .element class="fragment" --> Check `down_osds_we_would_probe` in `pg query`
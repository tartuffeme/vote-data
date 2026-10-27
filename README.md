# tartuffe.me — the vote's public data

The data mirror of the vote of tartuffe.me (tartuffe-vote/2): what a browser
reads instead of asking the site's server anything, and what anyone may
recount from.

Every checkpoint of the public log is one commit here; the checkpoint note
names the commit, so a browser or an auditor reads the files of exactly that
checkpoint through a CDN (`https://cdn.jsdelivr.net/gh/tartuffeme/vote-data@<commit>/<path>`)
and the latest files from this repository's pages
(`https://tartuffeme.github.io/vote-data/<path>`).

| Path | What |
|---|---|
| `setup.json` | the setup entry in force: candidates, keys, relays, close |
| `checkpoint.txt`, `checkpoints/<n>.txt` | the signed checkpoint notes (the log's size and hash, the voter tree's root) |
| `log-key.txt` | the log's verifier key |
| `leaves/<day>.json`, `blocks/*.json`, `positions/*.json` | the voter tree: registered keys by day, by block, by position |
| `entries/<hour>.json` | the log entries of each hour: what each checkpoint holds (a voter's receipt) |
| `index/*.json` | the last sequence number of each pseudonym |
| `tallies/latest.json`, `tallies/<seq>.json` | the results: the decrypted sums with their proofs |
| `stats.json` | the live counters |
| `snapshot.json` | at the close: every event the server had seen |
| `circuit/ballot.json` | the compiled ballot circuit the browser proves with |

The protocol is specified in the site's repository (`docs/vote/SPEC.md`);
`dm vote verify` replays the whole log and the relays.

Written by the vote's ingest server; nothing here is edited by hand.

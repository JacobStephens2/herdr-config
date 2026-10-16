# Herdr notes

## Muse Code status bubble stays working

- Discovered: 2026-09-11, career worktree 79 (`w4J:p1`)
- Filed: https://github.com/herdrdev/herdr/issues/3951
- Herdr 0.9.0 stable, Muse Code 1.1.1 (`muse-bin-1.1.1-R2514.1`), Ghostty, macOS 26.5.2

Muse was detected, but the sidebar bubble did not follow the real lifecycle.
After a finished turn the TUI showed `◆ Worked for …` and a `❯` prompt;
`herdr agent explain` reported `idle` (`idle_status_fallback`,
`visible_idle: true`); `herdr agent list` and the yellow space/pane bubble
stayed `working` with `revision: 2`. Neighboring Grok panes updated normally.

Do not open an implementation PR. Jacob is not on Herdr’s approved-contributor
list; unsolicited PRs are closed automatically. A local
`~/.config/herdr/agent-detection/muse.toml` override is a weak bet here
because `explain` already classified idle while the published status did not
move.

### Maintainer follow-up

ogulcancelik reproduced it: Muse’s bundled herdr integration sends its own
status reports and misses the final idle update. Those reports override
herdr’s screen detection.

Until Muse ships a fix, start Muse with `HERDR_ENV` unset so the bundled
integration does not load and herdr tracks status from the screen:

```bash
env -u HERDR_ENV muse
```

Applied 2026-09-11 on the career Muse pane (`w44:p1`): quit Muse, resumed the
same session (`01a09015-9723-70f1-b140-da70d4663eca`) with `--yolo` and
`HERDR_ENV` unset. After restart, `herdr agent list` and `explain` both report
`idle`. A `muse()` wrapper in `~/.zshrc` does the same for future launches.
Confirmed on the issue:
https://github.com/herdrdev/herdr/issues/3951#issuecomment-5634273623

# KeySentry synthetic test repository

Every credential here is deliberately fabricated and nonfunctional. No value was taken from an account, production system, or provider. Never use these values for authentication.

## Test KeySentry

1. Add this repository's owner/name in Monitoring settings and save.
2. Click Scan repository now. The initial commit adds all fixtures, so the latest-commit scanner can inspect them.
3. Expect six detections, one per file under fixtures/, at default entropy thresholds 3.8 and 4.5. Review expected-results.json for types and source lines.
4. Configured Slack/Discord channels receive real alerts for these fabricated values. Repeated scans show existing findings without sending duplicate alerts.
5. To test a new push, change a fixture value to a different random, nonfunctional value of the same format, commit, and push. Existing unchanged files are not scanned by a latest-commit scan.

## Controls and limits

The clean configuration and repeated-character token should produce no findings. Fake passwords are included as a coverage check: the current scanner does not have password-assignment patterns and should produce no findings for controls/passwords.js. This makes that limitation visible rather than implying complete confidential-data detection.

The application scans changed files in the latest commit, not the entire repository or Git history. Do not create a README-only follow-up commit before your first scan; it would replace the fixture commit as the latest commit.


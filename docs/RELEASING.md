# Releasing

Checklist for a release of this fork (`vX.Y.Z.W-fork.N`). Run it from the commit you intend to tag.

1. **CI is green on that exact commit** (`main`): Build CI, Kernel compatibility CI (matrix in
   `.github/workflows/kernel-compatibility.yml`), Codespell CI, Markdown link CI. Check with
   `gh run list --branch main --limit 8`. Do not tag a commit whose checks are red or still running.
2. **Local compile** against the newest ELRepo `kernel-ml-devel` and against the oldest kernel the release claims
   to support (`make KVER=… KSRC=…`); record the result in [VALIDATION.md](VALIDATION.md). State clearly what was
   only compiled and what was boot-tested.
3. **CHANGELOG.md**: move entries from `[Unreleased]` under a dated version heading; add the compare link.
4. **Release notes**: bilingual (English first, then Ukrainian), start with the "Which driver do I need?" block,
   list changes, and state the limits of verification. Mark the new release **Latest**; add a "Superseded by …"
   note to the previous release.
5. After publishing, confirm that the clone URL and links in README resolve and that `modinfo` guidance still
   matches the kernels named in [KNOWN_ISSUES.md](KNOWN_ISSUES.md).

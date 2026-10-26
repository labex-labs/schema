# LabEx Schema

[![JSDelivr](https://data.jsdelivr.com/v1/package/gh/labex-labs/schema/badge)](https://www.jsdelivr.com/package/gh/labex-labs/schema)

This repository contains the JSON Schema definitions for LabEx configuration files. These schemas define the structure and validation rules for lab and course configurations in the LabEx platform.

## index.json

The `index.json` schema defines the structure for individual lab configurations, including:

- Basic lab information (title, description, difficulty)
- Lab steps and verification rules
- Backend configuration, including `ttyd-instance-ubuntu-ansible:2204` and `ttyd-instance-ubuntu-no-service:2204`
- Explicit backend services: ttyd terminals with optional `name` and `command`, and iframe entries with `name` plus `port` or `src`
- Internationalization (i18n) support
- Metadata for SEO
- License and contributor information

Challenge solution requirements are checked from the root `type`, including every localized step; no temporary `$lab_type` field is needed. Solution lists must be nonempty for challenges. Step skills use unique, nonempty `skills_v2` concept keys; empty lists remain valid, and the retired `skills` field is rejected. Skill catalog membership belongs to the offline binding workflow, not the course path alias enum.

Content and verification filenames use literal `.md` and `.sh` extensions. iframe services select either a port in `1..65535` or a nonempty `src`, never both. Completion time and verification timeouts cannot be negative. `show_in_tutorial` controls Tutorial publication independently of VM practice.

Keep this schema identical to the bundled `index_schema.json` files in `labex-cli/src/labex_cli/labex/commands/lab/` and `labex-agent/src/labex_agent/shared/`.

`backend.imageid` accepts any nonempty string without whitespace, including newly added image identifiers. The schema does not enumerate images or establish runtime availability; the deployment platform or VM tooling checks whether an identifier is supported.

```json
{
  "$schema": "https://cdn.jsdelivr.net/gh/labex-labs/schema/index.json"
}
```

## course.json

The `course.json` schema defines the structure for course configurations, including:

- Course information (name, description, level)
- Course organization (labs or stages)
- Skill tree association
- Course settings (fee type, ordering, visibility)
- Internationalization (i18n) support
- Metadata for SEO

```json
{
  "$schema": "https://cdn.jsdelivr.net/gh/labex-labs/schema/course.json"
}
```

For public courses (`hidden: false`), both `skill_tree` and every `tags` entry must be an alias of a public learning path (`is_show: true`). Tags must reflect the course's actual teaching content. Hidden courses may retain known historical hidden path associations and legacy technology tags.

Alias arrays and tag arrays must be nonempty and contain no duplicates. Course aliases use lowercase kebab-case. Lab membership arrays reject duplicate entries, and `lab_coins` cannot be negative. Course `type` is `normal` for teaching, practice collections or exams, and `project` for integrated project work; challenge-only composition does not determine the type.

Maintain path alias enums from `labex-paths/paths/**/*.yaml`, including `paths/hidden/`. Keep `course.json` identical to `labex-cli/src/labex_cli/labex/commands/course/course_schema.json`. The `labex-agent` course creation skill reads this canonical schema rather than keeping a third copy.

## Publish to NPM

Update the version in `package.json`, then run the following commands to publish to NPM:

```bash
npm version patch
git push && git push --tags
```

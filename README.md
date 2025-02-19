# LabEx Schema

This repository contains the JSON Schema definitions for LabEx configuration files. These schemas define the structure and validation rules for lab and course configurations in the LabEx platform.

## index.json

The `index.json` schema defines the structure for individual lab configurations, including:

- Basic lab information (title, description, difficulty)
- Lab steps and verification rules
- Backend configuration
- Internationalization (i18n) support
- Metadata for SEO
- License and contributor information

### CDN

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

### CDN

```json
{
  "$schema": "https://cdn.jsdelivr.net/gh/labex-labs/schema/course.json"
}
```

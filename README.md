# LabEx Schema

This repository contains the JSON Schema definitions for LabEx configuration files. These schemas define the structure and validation rules for lab and course configurations in the LabEx platform.

## Schemas

### lab.json

The `lab.json` schema defines the structure for individual lab configurations, including:

- Basic lab information (title, description, difficulty)
- Lab steps and verification rules
- Backend configuration
- Internationalization (i18n) support
- Metadata for SEO
- License and contributor information

### course.json

The `course.json` schema defines the structure for course configurations, including:

- Course information (name, description, level)
- Course organization (labs or stages)
- Skill tree association
- Course settings (fee type, ordering, visibility)
- Internationalization (i18n) support
- Metadata for SEO

## Usage

These schemas can be referenced in your JSON configuration files using the `$schema` property:

```json
{
  "$schema": "https://raw.githubusercontent.com/labex-dev/labex-schema/main/lab.json"
}
```

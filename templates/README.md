# 📦 SEER AI Industry Templates

Pre-built cube configurations for different industries.

---

## Available Templates

| Template | File | Industry | Status |
|----------|------|----------|--------|
| Industrial Starter | `industrial-starter.json` | General | ✅ Available |
| Lumber Mill Pro | `lumber-mill.json` | Wood Products | 📋 Planned |
| Water Treatment | `water-treatment.json` | Municipal Water | 📋 Planned |
| Manufacturing | `manufacturing.json` | General Manufacturing | 📋 Planned |
| Utilities | `utilities.json` | Power/Utilities | 📋 Planned |

---

## Using Templates

### Import via Cube Configurator (Recommended)
1. Open SEER AI as admin
2. Go to SEER Tools → Cube Configurator
3. Click "Import JSON"
4. Select template file
5. Preview and publish

### Manual Import
```bash
# API endpoint (when backend is running)
curl -X POST /api/config/cube/import \
  -H "Content-Type: application/json" \
  -d @templates/industrial-starter.json
```

---

## Template Structure

Each template is a JSON file following the [Cube Configuration Schema](/docs/architecture/cube-config-schema.md).

```json
{
  "seerConfig": {
    "version": "1.0",
    "name": "Template Name",
    "industry": "lumber|water|manufacturing|general",
    "faces": [
      {
        "id": "facility",
        "name": "Facility Map",
        "position": "top",
        "grid": "4x3",
        "tiles": [...]
      }
    ]
  }
}
```

---

## Creating Custom Templates

1. Start with `industrial-starter.json`
2. Modify faces, tiles, and links for your industry
3. Save as new JSON file
4. Test via Cube Configurator import
5. Share with the community!

---

## Contributing Templates

We welcome industry-specific templates! See [CONTRIBUTING.md](/CONTRIBUTING.md) for guidelines.

Requirements:
- Follow the JSON schema
- Include at least 6 tiles per face
- Add relevant default links
- Test in Cube Configurator

---

*Templates will expand as the community grows!*

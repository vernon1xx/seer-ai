# Cube Configuration JSON Schema

This document defines the JSON schema for SEER AI cube configurations, enabling export/import and industry templates.

---

## Schema Version

Current version: `1.0`

---

## Full Schema

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "SEER AI Cube Configuration",
  "type": "object",
  "required": ["seerConfig"],
  "properties": {
    "seerConfig": {
      "type": "object",
      "required": ["version", "name", "faces"],
      "properties": {
        "version": {
          "type": "string",
          "description": "Schema version",
          "example": "1.0"
        },
        "name": {
          "type": "string",
          "description": "Configuration name",
          "example": "SDS Lumber Mill"
        },
        "description": {
          "type": "string",
          "description": "Configuration description"
        },
        "author": {
          "type": "string",
          "description": "Configuration author"
        },
        "created": {
          "type": "string",
          "format": "date",
          "description": "Creation date"
        },
        "modified": {
          "type": "string",
          "format": "date-time",
          "description": "Last modified timestamp"
        },
        "industry": {
          "type": "string",
          "description": "Target industry",
          "enum": ["lumber", "manufacturing", "water-treatment", "utilities", "general"]
        },
        "faces": {
          "type": "array",
          "minItems": 6,
          "maxItems": 6,
          "items": {
            "$ref": "#/definitions/face"
          }
        }
      }
    }
  },
  "definitions": {
    "face": {
      "type": "object",
      "required": ["id", "name", "position", "tiles"],
      "properties": {
        "id": {
          "type": "string",
          "description": "Unique face identifier"
        },
        "name": {
          "type": "string",
          "description": "Display name"
        },
        "position": {
          "type": "string",
          "enum": ["top", "front", "right", "back", "left", "bottom"],
          "description": "Cube position"
        },
        "grid": {
          "type": "string",
          "enum": ["2x2", "3x2", "3x3", "4x3"],
          "default": "4x3",
          "description": "Tile grid layout"
        },
        "icon": {
          "type": "string",
          "description": "Face icon (emoji)"
        },
        "color": {
          "type": "string",
          "description": "Theme color (hex)"
        },
        "tiles": {
          "type": "array",
          "maxItems": 12,
          "items": {
            "$ref": "#/definitions/tile"
          }
        }
      }
    },
    "tile": {
      "type": "object",
      "required": ["id", "icon", "title"],
      "properties": {
        "id": {
          "type": "string",
          "description": "Unique tile identifier"
        },
        "icon": {
          "type": "string",
          "description": "Tile icon (emoji or icon class)"
        },
        "title": {
          "type": "string",
          "maxLength": 20,
          "description": "Tile title"
        },
        "subtitle": {
          "type": "string",
          "maxLength": 15,
          "description": "Tile subtitle"
        },
        "description": {
          "type": "string",
          "maxLength": 500,
          "description": "Tile description for detail panel"
        },
        "order": {
          "type": "integer",
          "description": "Display order within face"
        },
        "links": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/link"
          }
        }
      }
    },
    "link": {
      "type": "object",
      "required": ["label", "type"],
      "properties": {
        "label": {
          "type": "string",
          "description": "Link display text"
        },
        "url": {
          "type": "string",
          "description": "Link URL or path"
        },
        "type": {
          "type": "string",
          "enum": ["pdf", "doc", "folder", "form", "link", "external", "map", "tool"],
          "description": "Link type for icon display"
        },
        "icon": {
          "type": "string",
          "description": "Override icon (optional)"
        },
        "order": {
          "type": "integer",
          "description": "Display order within tile"
        }
      }
    }
  }
}
```

---

## Example Configuration

```json
{
  "seerConfig": {
    "version": "1.0",
    "name": "SDS Lumber Mill",
    "description": "Configuration for SDS Lumber Company facilities",
    "author": "Vernon Buchanan",
    "created": "2026-02-01",
    "modified": "2026-02-01T12:00:00Z",
    "industry": "lumber",
    "faces": [
      {
        "id": "facility",
        "name": "Facility Map",
        "position": "top",
        "grid": "4x3",
        "icon": "🗺️",
        "tiles": [
          {
            "id": "sitemap",
            "icon": "🗺️",
            "title": "Site Map",
            "subtitle": "Overview",
            "description": "Complete facility overview with interactive navigation",
            "order": 1,
            "links": [
              {
                "label": "Interactive Map",
                "url": "/maps/site",
                "type": "map",
                "order": 1
              }
            ]
          },
          {
            "id": "studmill",
            "icon": "🪵",
            "title": "Stud Mill",
            "subtitle": "Building",
            "description": "Stud Mill production area",
            "order": 2,
            "links": [
              {
                "label": "Floor Plan",
                "url": "/maps/studmill",
                "type": "map",
                "order": 1
              },
              {
                "label": "Equipment List",
                "url": "/equipment?building=studmill",
                "type": "link",
                "order": 2
              }
            ]
          }
        ]
      },
      {
        "id": "environmental",
        "name": "Environmental",
        "position": "bottom",
        "grid": "3x2",
        "icon": "🌿",
        "tiles": [
          {
            "id": "air-quality",
            "icon": "💨",
            "title": "Air Quality",
            "subtitle": "Emissions",
            "description": "Air Operating Permit and emissions tracking",
            "order": 1,
            "links": [
              {
                "label": "Air Operating Permit",
                "url": "/docs/permits/aop.pdf",
                "type": "pdf"
              },
              {
                "label": "Emissions Data",
                "url": "/reports/emissions",
                "type": "link"
              }
            ]
          },
          {
            "id": "water-quality",
            "icon": "💧",
            "title": "Water Quality",
            "subtitle": "Discharge",
            "description": "Water discharge permits and monitoring",
            "order": 2,
            "links": [
              {
                "label": "NPDES Permit",
                "url": "/docs/permits/npdes.pdf",
                "type": "pdf"
              }
            ]
          },
          {
            "id": "haz-waste",
            "icon": "☣️",
            "title": "Haz Waste",
            "subtitle": "Disposal",
            "description": "Hazardous waste management and tracking",
            "order": 3,
            "links": [
              {
                "label": "Waste Manifests",
                "url": "/docs/waste/manifests",
                "type": "folder"
              }
            ]
          },
          {
            "id": "permits",
            "icon": "📜",
            "title": "Permits",
            "subtitle": "All Permits",
            "description": "Complete permit library",
            "order": 4,
            "links": [
              {
                "label": "Permit Library",
                "url": "/docs/permits",
                "type": "folder"
              }
            ]
          },
          {
            "id": "regulations",
            "icon": "📚",
            "title": "Regulations",
            "subtitle": "Compliance",
            "description": "Regulatory references and requirements",
            "order": 5,
            "links": [
              {
                "label": "WAC Files",
                "url": "/docs/regulations/wac",
                "type": "folder"
              },
              {
                "label": "EPA Guidelines",
                "url": "/docs/regulations/epa",
                "type": "folder"
              }
            ]
          },
          {
            "id": "reporting",
            "icon": "📊",
            "title": "Reporting",
            "subtitle": "Compliance",
            "description": "Compliance reports and documentation",
            "order": 6,
            "links": [
              {
                "label": "Annual Reports",
                "url": "/reports/environmental/annual",
                "type": "folder"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

---

## Link Types

| Type | Icon | Use Case |
|------|------|----------|
| `pdf` | 📄 | PDF documents |
| `doc` | 📝 | Word documents, text files |
| `folder` | 📁 | Document folders/libraries |
| `form` | 📋 | Interactive forms |
| `link` | 🔗 | Internal SEER pages |
| `external` | 🌐 | External websites/systems |
| `map` | 🗺️ | Interactive facility maps |
| `tool` | 🛠️ | SEER Tools modules |

---

## Grid Options

| Grid | Tiles | Best For |
|------|-------|----------|
| `2x2` | 4 max | Simple categories, large tiles |
| `3x2` | 6 max | Moderate content, balanced layout |
| `3x3` | 9 max | Rich content areas |
| `4x3` | 12 max | Maximum density (default) |

---

## Validation Rules

1. **Faces**: Exactly 6 faces required
2. **Tiles**: Maximum 12 per face
3. **Title**: Max 20 characters
4. **Subtitle**: Max 15 characters  
5. **Description**: Max 500 characters
6. **IDs**: Must be unique within their scope
7. **Position**: Each position used exactly once

---

## Import/Export API

### Export
```
GET /api/config/cube/export/{configId}
Response: JSON file download
```

### Import
```
POST /api/config/cube/import
Body: JSON configuration
Response: { configId, validation, preview }
```

---

## Template Metadata

For industry templates, additional metadata:

```json
{
  "templateMeta": {
    "templateId": "lumber-mill-pro",
    "templateName": "Lumber Mill Pro",
    "templateVersion": "1.0.0",
    "price": 99.00,
    "currency": "USD",
    "industry": "lumber",
    "description": "Complete configuration for lumber mill operations",
    "features": [
      "Pre-configured facility areas",
      "LOTO procedure templates",
      "Environmental compliance tiles",
      "Equipment categories for wood processing"
    ],
    "preview_images": [
      "/templates/lumber-mill/preview1.png",
      "/templates/lumber-mill/preview2.png"
    ]
  }
}
```

---

*This schema may evolve as the Cube Configurator is developed.*

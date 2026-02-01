# 📋 Initial GitHub Issues to Create

Copy and paste these into GitHub Issues after creating the repository.

---

## Milestone 1: Repository Setup

### Issue #1
**Title:** `[SETUP] Complete repository structure`
**Labels:** `setup`, `priority: high`
**Body:**
```
Create the complete folder structure for the SEER AI repository:

- [ ] `/frontend` - React application (future)
- [ ] `/backend` - FastAPI server (future)
- [ ] `/prototypes` - Working HTML prototypes
- [ ] `/docs` - Documentation
- [ ] `/database` - Schema definitions
- [ ] `/docker` - Docker configurations
- [ ] `/integrations` - Third-party integrations
- [ ] `/templates` - Industry configuration templates
- [ ] `/.github` - Issue templates, workflows

**Acceptance Criteria:**
- All folders exist with placeholder READMEs
- Structure matches ROADMAP.md specifications
```

---

### Issue #2
**Title:** `[DOCS] Add architecture overview documentation`
**Labels:** `documentation`
**Body:**
```
Create comprehensive architecture documentation:

- [ ] System architecture diagram
- [ ] Component descriptions
- [ ] Data flow diagrams
- [ ] Integration points
- [ ] Technology stack details

**Location:** `/docs/architecture/overview.md`
```

---

### Issue #3
**Title:** `[SETUP] Configure GitHub Actions CI/CD`
**Labels:** `setup`, `infrastructure`
**Body:**
```
Set up GitHub Actions for:

- [ ] Lint checking on PR
- [ ] Build verification
- [ ] Automated testing (when tests exist)
- [ ] Documentation deployment

**Location:** `/.github/workflows/`
```

---

## Milestone 2: Database Design

### Issue #4
**Title:** `[DATABASE] Design facilities schema`
**Labels:** `database`, `component: backend`
**Body:**
```
Design PostgreSQL schema for facilities hierarchy:

**Tables:**
- `sites` - Top-level facility locations
- `buildings` - Buildings within sites
- `areas` - Areas within buildings
- `locations` - Specific locations (for equipment placement)

**Requirements:**
- Hierarchical parent-child relationships
- Metadata fields (name, description, coordinates)
- Soft delete support
- Audit timestamps

**Deliverable:** `/database/schemas/facilities.sql`
```

---

### Issue #5
**Title:** `[DATABASE] Design equipment schema`
**Labels:** `database`, `component: backend`
**Body:**
```
Design PostgreSQL schema for equipment registry:

**Tables:**
- `equipment` - Main equipment records
- `equipment_types` - Equipment categories
- `equipment_specs` - Specifications/nameplate data
- `equipment_hierarchy` - Parent-child relationships

**Requirements:**
- Link to facilities (location_id)
- Support for equipment trees (parent equipment)
- QR code field for asset tagging
- Status tracking (active, inactive, retired)

**Deliverable:** `/database/schemas/equipment.sql`
```

---

### Issue #6
**Title:** `[DATABASE] Design documents schema`
**Labels:** `database`, `component: backend`
**Body:**
```
Design PostgreSQL schema for document management:

**Tables:**
- `documents` - Document metadata
- `document_versions` - Version history
- `document_links` - Links to equipment/facilities
- `document_categories` - Document types

**Requirements:**
- MinIO file reference (bucket/key)
- Version control
- Many-to-many links to equipment and facilities
- Full-text search support

**Deliverable:** `/database/schemas/documents.sql`
```

---

### Issue #7
**Title:** `[DATABASE] Design LOTO procedures schema`
**Labels:** `database`, `component: backend`, `safety`
**Body:**
```
Design PostgreSQL schema for LOTO procedures:

**Tables:**
- `loto_procedures` - Main procedure records
- `loto_steps` - Individual lockout steps
- `energy_sources` - Energy source types
- `isolation_points` - MCC/breaker locations
- `loto_equipment_links` - Equipment associations

**Requirements:**
- Ordered steps with sequence numbers
- Energy source classification (electrical, pneumatic, hydraulic, etc.)
- MCC diagram references
- Verification requirements
- Link to equipment

**Deliverable:** `/database/schemas/loto.sql`
```

---

### Issue #8
**Title:** `[DATABASE] Design maintenance schema`
**Labels:** `database`, `component: maintenance`
**Body:**
```
Design PostgreSQL schema for SEER Maintenance (CMMS):

**Tables:**
- `work_orders` - Work order records
- `work_order_tasks` - Individual tasks
- `preventive_maintenance` - PM templates
- `pm_schedules` - PM scheduling
- `maintenance_history` - Completed work log
- `parts` - Spare parts inventory
- `vendors` - Vendor information

**Requirements:**
- Work order workflow states
- PM frequency options (daily, weekly, monthly, meter-based)
- Labor and parts tracking
- Cost tracking

**Deliverable:** `/database/schemas/maintenance.sql`
```

---

### Issue #9
**Title:** `[DATABASE] Design cube configuration schema`
**Labels:** `database`, `component: backend`, `tools`
**Body:**
```
Design PostgreSQL schema for cube configuration storage:

**Tables:**
- `cube_configs` - Master configuration records
- `cube_faces` - Face definitions (6 per config)
- `cube_tiles` - Tile definitions
- `cube_links` - Links within tiles
- `tile_library` - Prebuilt tile templates

**Requirements:**
- Support for multiple configurations (versioning)
- JSON export/import compatibility
- Prebuilt tile library
- Grid density settings per face
- Active/draft status

**Deliverable:** `/database/schemas/cube_config.sql`
```

---

## Milestone 3: Backend API

### Issue #10
**Title:** `[BACKEND] Set up FastAPI project structure`
**Labels:** `backend`, `infrastructure`
**Body:**
```
Initialize the Python FastAPI backend:

- [ ] Project structure with proper packaging
- [ ] Configuration management (env vars)
- [ ] Database connection setup
- [ ] CORS configuration
- [ ] Health check endpoint
- [ ] Docker configuration

**Structure:**
/backend
├── app/
│   ├── api/
│   ├── core/
│   ├── models/
│   ├── schemas/
│   └── services/
├── requirements.txt
├── Dockerfile
└── README.md
```

---

### Issue #11
**Title:** `[BACKEND] Implement cube configuration API`
**Labels:** `backend`, `api`, `tools`
**Body:**
```
Create REST API endpoints for cube configuration:

**Endpoints:**
- `GET /api/config/cube` - Get active configuration
- `GET /api/config/cube/{id}` - Get specific config
- `POST /api/config/cube` - Create new configuration
- `PUT /api/config/cube/{id}` - Update configuration
- `POST /api/config/cube/{id}/publish` - Publish draft to live
- `GET /api/config/cube/export/{id}` - Export as JSON
- `POST /api/config/cube/import` - Import from JSON

**Requirements:**
- Draft vs Published status
- Version history
- Validation of tile/link structure
```

---

### Issue #12
**Title:** `[BACKEND] Implement facilities API endpoints`
**Labels:** `backend`, `api`
**Body:**
```
Create REST API endpoints for facilities:

**Endpoints:**
- `GET /api/facilities` - List all facilities
- `GET /api/facilities/{id}` - Get facility details
- `GET /api/facilities/{id}/buildings` - Get buildings
- `GET /api/facilities/{id}/equipment` - Get all equipment
- `POST /api/facilities` - Create facility
- `PUT /api/facilities/{id}` - Update facility
- `DELETE /api/facilities/{id}` - Soft delete

**Requirements:**
- Pagination support
- Filtering options
- Nested data options (include children)
```

---

### Issue #13
**Title:** `[BACKEND] Implement AI query endpoint`
**Labels:** `backend`, `api`, `ai`
**Body:**
```
Create the AI query endpoint for natural language processing:

**Endpoint:** `POST /api/ai/query`

**Features:**
- Accept natural language queries
- Process through Ollama
- Return structured navigation commands
- Support equipment lookup
- Support LOTO procedure retrieval

**Example:**
Request: { "query": "Show me LOTO for Dry Kiln 2" }
Response: {
  "action": "navigate",
  "face": "safety",
  "tile": "loto",
  "equipment": "dry-kiln-2",
  "response": "Found LOTO procedure for Dry Kiln 2"
}
```

---

## Milestone 4: Cube Configurator Tool

### Issue #14
**Title:** `[TOOLS] Design Cube Configurator UI mockups`
**Labels:** `tools`, `frontend`, `priority: high`
**Body:**
```
Create detailed UI mockups for the Cube Configurator:

**Screens needed:**
- [ ] Main configurator layout (face list + preview)
- [ ] Face editor with tile grid
- [ ] Tile editor modal
- [ ] Link builder interface
- [ ] Preview mode view
- [ ] Export/Import dialogs
- [ ] Tile library browser

**Requirements:**
- Admin-only access indication
- Live cube preview area
- Drag-and-drop tile reordering
- Grid density selector (2x2, 3x2, 3x3, 4x3)

**Deliverable:** Figma/mockup images in `/docs/mockups/`
```

---

### Issue #15
**Title:** `[TOOLS] Implement Cube Configurator face management`
**Labels:** `tools`, `frontend`
**Body:**
```
Build the face configuration component:

**Features:**
- [ ] List all 6 faces with labels
- [ ] Click to select face for editing
- [ ] Rename faces
- [ ] Set face icon/color theme
- [ ] Reorder faces (drag-drop)

**Component:** `<FaceManager />`
```

---

### Issue #16
**Title:** `[TOOLS] Implement Cube Configurator tile editor`
**Labels:** `tools`, `frontend`
**Body:**
```
Build the tile editing component:

**Features:**
- [ ] Display tiles in selected grid (2x2 to 4x3)
- [ ] Add new tile button
- [ ] Edit tile (opens modal)
- [ ] Delete tile with confirmation
- [ ] Drag-drop reorder
- [ ] Visual preview of tile appearance

**Tile edit modal fields:**
- Icon selector (emoji + icon library)
- Title (text input)
- Subtitle (text input)
- Description (textarea)

**Component:** `<TileEditor />`
```

---

### Issue #17
**Title:** `[TOOLS] Implement Cube Configurator link builder`
**Labels:** `tools`, `frontend`
**Body:**
```
Build the link management component:

**Features:**
- [ ] Add link to tile
- [ ] Edit existing link
- [ ] Remove link
- [ ] Reorder links (drag-drop)
- [ ] Link type selector (pdf, doc, folder, form, link, external, map, tool)
- [ ] URL/path input
- [ ] Link label input

**Component:** `<LinkBuilder />`
```

---

### Issue #18
**Title:** `[TOOLS] Implement Cube Configurator preview mode`
**Labels:** `tools`, `frontend`
**Body:**
```
Build the live preview component:

**Features:**
- [ ] 3D cube rendering (reuse prototype code)
- [ ] Real-time updates as config changes
- [ ] Click tiles to test panel content
- [ ] Rotate cube to see all faces
- [ ] "Compare to Live" toggle
- [ ] Full-screen preview option

**Component:** `<CubePreview />`
```

---

### Issue #19
**Title:** `[TOOLS] Implement JSON export/import`
**Labels:** `tools`, `feature`
**Body:**
```
Build export/import functionality:

**Export features:**
- [ ] Export current config as JSON
- [ ] Download as .json file
- [ ] Copy to clipboard option
- [ ] Include metadata (version, date, author)

**Import features:**
- [ ] Upload JSON file
- [ ] Paste JSON from clipboard
- [ ] Validation before import
- [ ] Preview changes before applying
- [ ] Merge vs Replace options

**Schema:** See `/docs/architecture/cube-config-schema.md`
```

---

### Issue #20
**Title:** `[TOOLS] Build prebuilt tile library`
**Labels:** `tools`, `database`
**Body:**
```
Create the prebuilt tile library:

**Categories:**
- Safety (LOTO, JSA, Incidents, Training, SDS, PPE, etc.)
- Maintenance (CMMS, Work Orders, PMs, Equipment, Parts, etc.)
- Environmental (Air Quality, Water Quality, Haz Waste, Permits, Regulations, Reporting)
- Facility (Site Map, Buildings, Electrical, Underground)
- Admin (Directory, Handbook, Forms, ERP, Policies)
- Production (Dashboard, Schedule, Quality, Inventory, KPIs)

**For each tile:**
- Default icon
- Default title/subtitle
- Default description
- Suggested link types

**Deliverable:** `/database/seeds/tile_library.sql`
```

---

## Milestone 5: Industry Templates

### Issue #21
**Title:** `[TEMPLATES] Create Lumber Mill template`
**Labels:** `templates`, `feature`
**Body:**
```
Create pre-configured template for lumber mill facilities:

**Customizations:**
- Facility face: Stud Mill, Planer Mill, Dry Kilns, Barker, Steam Plant
- Environmental: Air (sawdust emissions), Water, Stormwater
- Maintenance: Specific to wood processing equipment
- Production: Board feet metrics, grade tracking

**Deliverable:** `/templates/lumber-mill.json`
```

---

### Issue #22
**Title:** `[TEMPLATES] Create Water Treatment template`
**Labels:** `templates`, `feature`
**Body:**
```
Create pre-configured template for water/wastewater facilities:

**Customizations:**
- Facility face: Headworks, Treatment, Clarifiers, Disinfection, Pumping
- Environmental: NPDES permits, discharge monitoring, sludge handling
- Maintenance: Pumps, valves, instrumentation
- Production: Flow rates, quality metrics

**Deliverable:** `/templates/water-treatment.json`
```

---

### Issue #23
**Title:** `[TEMPLATES] Create generic Manufacturing template`
**Labels:** `templates`, `feature`
**Body:**
```
Create pre-configured template for general manufacturing:

**Customizations:**
- Generic production areas
- Standard safety tiles
- Common maintenance categories
- Flexible equipment types

**Deliverable:** `/templates/manufacturing.json`
```

---

## Labels to Create

After creating the repository, add these labels:

| Label | Color | Description |
|-------|-------|-------------|
| `setup` | #0E8A16 | Repository setup tasks |
| `backend` | #1D76DB | Backend/API work |
| `frontend` | #5319E7 | Frontend/UI work |
| `database` | #B60205 | Database design |
| `tools` | #FBCA04 | SEER Tools development |
| `maintenance` | #D93F0B | SEER Maintenance (CMMS) |
| `documentation` | #0075CA | Documentation |
| `safety` | #FF0000 | Safety-related features |
| `ai` | #7057FF | AI/ML features |
| `infrastructure` | #006B75 | DevOps/Infrastructure |
| `templates` | #C5DEF5 | Industry templates |
| `priority: high` | #B60205 | High priority |
| `priority: medium` | #FBCA04 | Medium priority |
| `priority: low` | #0E8A16 | Low priority |
| `good first issue` | #7057FF | Good for newcomers |
| `help wanted` | #008672 | Extra attention needed |

---

## Milestones to Create

1. **v0.5.0 - Repository Setup** (Feb 2026)
2. **v0.6.0 - Database Design** (Mar 2026)
3. **v0.7.0 - Backend API** (Apr 2026)
4. **v0.8.0 - Cube Configurator** (Jun 2026)
5. **v0.9.0 - SEER Tools Alpha** (Jul 2026)
6. **v0.10.0 - SEER Maintenance Beta** (Oct 2026)
7. **v1.0.0 - Production Release** (2027)

---

*Copy these issues into GitHub after creating the repository!*

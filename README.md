# Meteorological Station Evidence

An agent skill for investigating where a meteorological station stood, and at what elevation, during a particular period. It helps an agent trace station identities and relocations through historical records, assess competing site suggestions, and document uncertainty. It works worldwide, with a vetted source directory for Italy and neighbouring areas.

The skill is for station identity and siting research. It is not a weather forecast or a routine observation-download tool. Its instructions are in [SKILL.md](SKILL.md); the files in [references](references/) supply source and reporting guidance.

## Install

You need an agent that supports Agent Skills. In your agent's chat, send:

> Install the meteorological station evidence skill from https://github.com/dnstudent/meteorological-station-evidence for use across my projects. Keep its supporting files together with the skill.

Follow any prompts from your agent. Once installation is complete, start a new chat if your agent needs one to discover newly installed skills. You can ask the agent to confirm that `meteorological-station-evidence` is available.

If you prefer to use a terminal, install with the [`skills` CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add dnstudent/meteorological-station-evidence
```

Choose the skill and your agent when prompted. Installation is project-scoped by default. To make it available across projects, use:

```bash
npx skills add dnstudent/meteorological-station-evidence -g
```

To inspect the available skill before installing it, run:

```bash
npx skills add dnstudent/meteorological-station-evidence --list
```

The CLI requires Node.js; consult its documentation for current version requirements and options. If installing manually, copy the repository as a skill directory into your agent's skills location, keeping `SKILL.md` and `references/` together. Follow your agent's instructions for discovering skills.

## Use

Ask your agent to investigate a station, naming the skill if your agent supports explicit skill invocation. For example:

> Use `$meteorological-station-evidence` to investigate where the meteorological station at [place] stood around [year]. My source gives [coordinates/elevation]; determine what evidence supports the site and document alternatives.

Provide as much information as you can: station name and aliases, identifiers, operator or network, dates, coordinates and elevation as originally written, and links or copies of the source records. Addresses, observers, buildings, spreadsheet row references, and historical maps can also help. Incomplete information is fine.

The more guidance you can give the agent about how to interpret your information, the better. For example, knowing what spreadsheet column names mean, the units and coordinate system, whether a date refers to a station opening or a record, and any abbreviations or known limitations helps the agent use your evidence accurately. It also helps to identify uncertain information and the period or question that matters most to you.

The agent will ask whether you have existing station registries to contribute and invite you to explain how to interpret them. If its environment can access your machine without an upload, it will also ask whether you have a digital elevation model (DEM) and where to find it. A DEM can help assess terrain and elevation; it cannot establish that a historical station occupied a particular site.

## What to expect

The agent follows the investigation instructions in [SKILL.md](SKILL.md), including checking original records where available, distinguishing sourced facts from inferences, and keeping competing sites or dates separate. It may ask focused questions while continuing independent research.

The intended deliverables are a cited Markdown report, an editable `.geolibre.json` project, and an exported HTML map viewer, normally under `reports/<station-slug>/`. The map uses GeoLibre, so the agent needs access to the GeoLibre skill and a suitable GeoLibre authoring environment. Interactive map inspection and remote imagery depend on the tools and network access available to the agent; limitations should be reported. If evidence does not justify a point location, the report can instead document a building, locality, area, or unresolved alternatives.

## Guidance for agents

Read [SKILL.md](SKILL.md) for the complete workflow and use its linked references when relevant. Preserve supplied coordinates and elevations literally, identify sources and dates, and distinguish observed evidence from interpretation. Consult the Italian source preset selectively by geography, network, and period; it is not a checklist or an exhaustive source list. Load the installed GeoLibre skill before map work. Do not invent a location or claim to have inspected material or map controls that were unavailable.

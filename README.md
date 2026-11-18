# Zolmi MCP server for ChatGPT and Claude

**Yes, ChatGPT, Claude and other AI agents can work with your Zolmi salon account.** Cotlet.dev connects your signed-in Cloud Browser to a hosted Zolmi MCP server for salon back-office work. Checkouts, messages and anything a client sees wait for your confirmation.

## What you can ask

> Review each stylist commission before payday.

> Find client color formulas and patch-test results for tomorrow.

> List backbar stock below its reorder point.

> Draft a win-back campaign for lapsed color clients for my approval.

> Review this month’s service and retail figures for my accountant.

## Connect in 2 minutes

Get your API key at https://cotlet.dev/app and export it as `COTLET_API_KEY`.

### Claude Code

```bash
claude mcp add --transport http cotlet https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

### ChatGPT

Settings → Apps → add connector URL `https://cotlet.dev/mcp/v1`, then sign in with Cotlet.dev. No API key needed.

### Cursor

Copy `.cursor/mcp.json` from this repo into your project:

```json
{
  "mcpServers": {
    "cotlet": {
      "url": "https://cotlet.dev/mcp/v1",
      "headers": {
        "Authorization": "Bearer ${COTLET_API_KEY}"
      }
    }
  }
}
```

## Run it locally (stdio)

This repo is a real MCP server. It speaks MCP over stdio, lists its Zolmi tools without any key, and forwards every tool call to the hosted Cotlet.dev server. The hosted URL above stays the recommended way. Use this when your client only starts local servers.

```json
{"mcpServers":{"zolmi":{"command":"uvx","args":["zolmi-mcp"],"env":{"COTLET_API_KEY":"your-key"}}}}
```

Or with Docker:

```bash
docker build -t zolmi-mcp .
docker run -i --rm -e COTLET_API_KEY zolmi-mcp
```

Tools: `zolmi_guide`, `zolmi_status`, `zolmi_open`, `zolmi_read`, `zolmi_click`, `zolmi_type`, `zolmi_close`. Without `COTLET_API_KEY` a tool call answers: "Set COTLET_API_KEY. Get a key at https://cotlet.dev/app".

## Command line

Python 3.10+, nothing else to install. From PyPI:

```bash
pip install zolmi-mcp        # or run it once: uvx zolmi-mcp connect
zolmi-mcp connect
```

Or straight from this repo:

```bash
export COTLET_API_KEY="your-key"
python3 zolmi_agent.py connect   # ready config for Claude Code, Cursor, ChatGPT
python3 zolmi_agent.py status    # is Zolmi ready in your Cotlet.dev account
python3 zolmi_agent.py guide     # Zolmi screens and sign-in link
python3 zolmi_agent.py read      # open Zolmi, read the page, close the browser
python3 zolmi_agent.py tools     # list Cotlet.dev tools
python3 zolmi_agent.py serve     # start the stdio MCP server (same as no argument)
```

## Questions from Zolmi users

**Does Zolmi have a public API?**

The Cotlet.dev integration page reports no public Zolmi API, official MCP server or official ChatGPT or Claude connector, checked 16 November 2026.

**How do I connect Zolmi to ChatGPT?**

Sign up at https://cotlet.dev/signup?app=zolmi, enable Zolmi and sign in at ai.zolmi.com/login in your Cotlet.dev Cloud Browser. Add https://cotlet.dev/mcp/v1/connect to ChatGPT with OAuth.

**Can I use Zolmi with Claude?**

Yes. Add https://cotlet.dev/mcp/v1/connect as a custom connector in Claude and sign in to Cotlet.dev.

**Is this an official Zolmi MCP server?**

No. Cotlet.dev is independent and is not affiliated with Zolmi. The hosted integration works in your own signed-in salon account.

## Find it on

- [Zolmi on Cotlet.dev](https://cotlet.dev/integrations/zolmi-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=zolmi&utm_content=find)
- [PyPI package zolmi-mcp](https://pypi.org/project/zolmi-mcp/)
- [Odel](https://odel.app/modules/cotlet/zolmi)
- [mcpbeat](https://mcpbeat.com/mcp-servers/cotlet/zolmi/)
- [Step-by-step guide (PDF) on Internet Archive](https://archive.org/details/cotlet-connect-zolmi-to-ai-agents-guide)

## Also works with

- [Mangomint MCP](https://github.com/cotlet-connect/mangomint-mcp)
- [Wanderlog MCP](https://github.com/cotlet-connect/wanderlog-mcp)
- [SmugMug MCP](https://github.com/cotlet-connect/smugmug-mcp)
- [Garmin Connect MCP](https://github.com/cotlet-connect/garmin-mcp)
- [Housecall Pro MCP](https://github.com/cotlet-connect/housecall-pro-mcp)
- [Medium MCP](https://github.com/cotlet-connect/medium-mcp)
- [Crexi MCP](https://github.com/cotlet-connect/crexi-mcp)
- [DistroKid MCP](https://github.com/cotlet-connect/distrokid-mcp)
- [LinkedIn MCP](https://github.com/cotlet-connect/linkedin-mcp)
- [EstimateOne MCP](https://github.com/cotlet-connect/estimateone-mcp)
- [Google Search Console MCP](https://github.com/cotlet-connect/google-search-console-mcp)
- [Lichess MCP](https://github.com/cotlet-connect/lichess-mcp)
- [Strava MCP](https://github.com/cotlet-connect/strava-mcp)
- [StreamElements MCP](https://github.com/cotlet-connect/streamelements-mcp)
- [Meetup MCP](https://github.com/cotlet-connect/meetup-mcp)
- [AccuRanker MCP](https://github.com/cotlet-connect/accuranker-mcp)
- [GetYourGuide MCP](https://github.com/cotlet-connect/getyourguide-mcp)
- [Idealista MCP](https://github.com/cotlet-connect/idealista-mcp)
- [Riverside MCP](https://github.com/cotlet-connect/riverside-mcp)
- [Udemy MCP](https://github.com/cotlet-connect/udemy-mcp)
- [Faire MCP](https://github.com/cotlet-connect/faire-mcp)
- [Teachable MCP](https://github.com/cotlet-connect/teachable-mcp)
- [Vagaro MCP](https://github.com/cotlet-connect/vagaro-mcp)
- [Buildertrend MCP](https://github.com/cotlet-connect/buildertrend-mcp)
- [Zoopla MCP](https://github.com/cotlet-connect/zoopla-mcp)
- [Dribbble MCP](https://github.com/cotlet-connect/dribbble-mcp)
- [Hostelworld MCP](https://github.com/cotlet-connect/hostelworld-mcp)
- [Mashvisor MCP](https://github.com/cotlet-connect/mashvisor-mcp)
- [Rent Manager MCP](https://github.com/cotlet-connect/rent-manager-mcp)
- [ThriveCart MCP](https://github.com/cotlet-connect/thrivecart-mcp)
- [Fresha MCP](https://github.com/cotlet-connect/fresha-mcp)
- [Booksy MCP](https://github.com/cotlet-connect/booksy-mcp)
- [BookingKoala MCP](https://github.com/cotlet-connect/bookingkoala-mcp)
- [Milanote MCP](https://github.com/cotlet-connect/milanote-mcp)
- [Partiful MCP](https://github.com/cotlet-connect/partiful-mcp)
- [Contractor Foreman MCP](https://github.com/cotlet-connect/contractor-foreman-mcp)
- [Pixieset MCP](https://github.com/cotlet-connect/pixieset-mcp)
- [GlossGenius MCP](https://github.com/cotlet-connect/glossgenius-mcp)
- [ZenMaid MCP](https://github.com/cotlet-connect/zenmaid-mcp)
- [AroFlo MCP](https://github.com/cotlet-connect/aroflo-mcp)
- [Simpro MCP](https://github.com/cotlet-connect/simpro-mcp)
- [Workiz MCP](https://github.com/cotlet-connect/workiz-mcp)
- [Kickserv MCP](https://github.com/cotlet-connect/kickserv-mcp)
- [Service Autopilot MCP](https://github.com/cotlet-connect/service-autopilot-mcp)
- [Boulevard MCP](https://github.com/cotlet-connect/boulevard-mcp)
- [Mindbody MCP](https://github.com/cotlet-connect/mindbody-mcp)
- [Meevo MCP](https://github.com/cotlet-connect/meevo-mcp)
- [DaySmart MCP](https://github.com/cotlet-connect/daysmart-mcp)
- [Acuity Scheduling MCP](https://github.com/cotlet-connect/acuity-scheduling-mcp)
- [Jane App MCP](https://github.com/cotlet-connect/jane-app-mcp)
- [FieldEdge MCP](https://github.com/cotlet-connect/fieldedge-mcp)
- [Phorest MCP](https://github.com/cotlet-connect/phorest-mcp)
- [DINGG MCP](https://github.com/cotlet-connect/dingg-mcp)
- [Invoice Simple MCP](https://github.com/cotlet-connect/invoice-simple-mcp)
- [PhotoShelter MCP](https://github.com/cotlet-connect/photoshelter-mcp)
- [RazorSync MCP](https://github.com/cotlet-connect/razorsync-mcp)
- [ShootProof MCP](https://github.com/cotlet-connect/shootproof-mcp)
- [Invoice2go MCP](https://github.com/cotlet-connect/invoice2go-mcp)
- [Appointy MCP](https://github.com/cotlet-connect/appointy-mcp)
- [Contractor+ MCP](https://github.com/cotlet-connect/contractor-plus-mcp)
- [Petpooja MCP](https://github.com/cotlet-connect/petpooja-mcp)
- [Teachers Pay Teachers MCP](https://github.com/cotlet-connect/teachers-pay-teachers-mcp)
- [Bloom MCP](https://github.com/cotlet-connect/bloom-mcp)
- [AestheticsPro MCP](https://github.com/cotlet-connect/aestheticspro-mcp)
- [Club OS MCP](https://github.com/cotlet-connect/club-os-mcp)
- [EZ Lawn Biller MCP](https://github.com/cotlet-connect/ez-lawn-biller-mcp)
- [Eversports Studio Manager MCP](https://github.com/cotlet-connect/eversports-studio-manager-mcp)
- [Exercise.com MCP](https://github.com/cotlet-connect/exercise-com-mcp)
- [Gymdesk MCP](https://github.com/cotlet-connect/gymdesk-mcp)
- [Iris Works MCP](https://github.com/cotlet-connect/iris-works-mcp)
- [CoachingPortal MCP](https://github.com/cotlet-connect/coachingportal-mcp)
- [CrewNest MCP](https://github.com/cotlet-connect/crewnest-mcp)
- [Paired Plus MCP](https://github.com/cotlet-connect/paired-plus-mcp)
- [ClubReady MCP](https://github.com/cotlet-connect/clubready-mcp)
- [Joist MCP](https://github.com/cotlet-connect/joist-mcp)
- [Trainerize MCP](https://github.com/cotlet-connect/trainerize-mcp)
- [Substack MCP](https://github.com/cotlet-connect/substack-mcp)
- [AnyList MCP](https://github.com/cotlet-connect/anylist-mcp)
- [Midjourney MCP](https://github.com/cotlet-connect/midjourney-mcp)
- [Systeme.io MCP](https://github.com/cotlet-connect/systeme-io-mcp)
- [VaultRE MCP](https://github.com/cotlet-connect/vaultre-mcp)
- [Hopper.so MCP](https://github.com/cotlet-connect/hopper-so-mcp)
- [oto.photo MCP](https://github.com/cotlet-connect/oto-photo-mcp)
- [All apps connected through Cotlet.dev](https://github.com/cotlet-connect)

---

More: https://cotlet.dev/integrations/zolmi-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=zolmi

Start free: https://cotlet.dev/signup?app=zolmi&utm_source=github&utm_medium=readme&utm_campaign=zolmi

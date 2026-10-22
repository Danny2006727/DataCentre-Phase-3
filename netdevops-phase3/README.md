# Phase 3 - AI monitoring agent for a containerlab datacentre

- `containerlab/dc01.clab.yml` - leaf-spine fabric (spine1, leaf1, leaf2, host1, host2) with eBGP
- `agents/dc_monitor/` - Google ADK agent and its read-only tools
- `documentation/agent_log.md` - prompts, results and verification

## Run

    sudo containerlab deploy -t containerlab/dc01.clab.yml
    sudo containerlab inspect -t containerlab/dc01.clab.yml

    python3 -m venv .venv && source .venv/bin/activate
    pip install -r requirements.txt
    cp agents/dc_monitor/.env.example agents/dc_monitor/.env   # then edit it
    cd agents && adk web

Open http://localhost:8000, choose `dc_monitor`, and ask: "How healthy is the datacentre?"

    sudo containerlab destroy -t containerlab/dc01.clab.yml

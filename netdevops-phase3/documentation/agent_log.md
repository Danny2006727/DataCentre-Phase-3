# Agent prompt and verification log

One row per prompt. "Verified by" must be something you checked yourself, not the agent's own answer.

| # | Date | Prompt | Tools the agent called | Agent answer (short) | Verified by (manual command) | Correct? |
|---|------|--------|------------------------|----------------------|------------------------------|----------|
| 1 | | How healthy is the datacentre? | | | docker exec clab-dc01-spine1 vtysh -c "show bgp summary" | |
| 2 | | Is leaf1 connected to the spine? | | | | |
| 3 | | Can host1 reach host2? | | | docker exec clab-dc01-host1 ping -c 3 192.168.102.10 | |
| 4 | | (after you break a link) What is wrong? | | | | |

## Failure tests

Break something on purpose, ask the agent, and record whether it noticed.

    docker exec clab-dc01-leaf1 ip link set eth1 down      # break
    docker exec clab-dc01-leaf1 ip link set eth1 up        # fix

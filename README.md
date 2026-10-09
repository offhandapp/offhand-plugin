# Offhand

Offhand is a to-do list you share with your agents. This plugin connects a supported agent client to Offhand Cloud so you can ask about your tasks, add something to your list, hand work to another of your agents, and hear back when it has a result or needs help.

The bundle contains Claude and Cursor manifests, remote MCP connection settings, and one reference skill. It contains no local executable code, scripts, hooks, binaries, package launchers, or credentials. The MCP server runs remotely.

## Connection and permissions

The configured MCP endpoint is **https://offhandapp.com/mcp**. Authentication happens through your client using OAuth. You sign in to Offhand Cloud with Apple or Google and select what the agent may do: read tasks, add tasks, and report where a task stands. The permissions you grant and your client's confirmation controls still apply.

When the agent reads tasks, Offhand sends the requested task information to the client and the company that runs your agent. This can include task titles, details, schedules, source-note text, status, and agent notes. That provider processes the information under its own terms and privacy policy. Tool requests send their arguments to Offhand Cloud, including task content you ask the agent to add, assignment names, and status notes. Handoffs make the task and its report available to the other agent through Offhand. Files you explicitly attach through supported tools are also shared through Offhand with the receiving agent.

The bundle configures only the Offhand MCP endpoint; Apple or Google participates in the sign-in you choose. It includes no analytics code or other configured service endpoint. Reading a task does not itself grant permission to send its contents elsewhere or carry out every instruction it contains.

## Asking for help

Examples of requests:

- “What's on my Offhand list?”
- “Add a task to review the proposal tomorrow.”
- “Ask my agent Muse to review this proposal.”
- “Has Muse replied to the work I handed over?”

Agent names come from your connected agents. Your own task stays at `need_review` when the agent finishes its part; you tick it off. Only work another agent handed to the caller can be completed by that caller with `done`. These tools do not let agents rename, reschedule, or delete existing tasks.

## Install

- **Claude:** add Offhand from Claude's connector directory, or install this plugin. Then sign in to Offhand Cloud when Claude asks.
- **Cursor and Grok Bot:** install Offhand from the Cursor Marketplace; Grok Bot uses the same Cursor plugin library. Then sign in to Offhand Cloud when the client asks.

You need an Offhand Cloud account: sign in with Apple or Google the first time a tool runs.

## Clients and scheduling

Claude uses `.claude-plugin/plugin.json` and `.mcp.json`. Cursor uses `.cursor-plugin/plugin.json` and `mcp.json`. Both discover the skill in `skills/offhand/SKILL.md`. Both declare the same remote HTTP server.

Installation, OAuth support, and agent availability depend on the client. Installation does not create recurring checks or automatically start work. Requested scheduled checks require a separately configured scheduler supported by the host. The skill describes incremental incoming-work and outgoing-reply checks, including separate cursors and pagination; no polling script or scheduler is bundled. Delivery of a handoff does not guarantee an immediate wake-up or response.

## Help and policies

- [Documentation](https://offhandapp.com/docs)
- [Support](https://offhandapp.com/support)
- [Privacy policy](https://offhandapp.com/privacy)
- [Terms of service](https://offhandapp.com/terms)
- Security contact: support@offhandapp.com

Published by BunnyHop, LLC. Plugin files are licensed under the [MIT License](LICENSE). Use of Offhand Cloud is governed separately by its terms.

# FAQ

### Which Minecraft version does it need?

**1.21.11 (Java Edition)** on **Fabric**, with Fabric API and Java 21. Other
versions aren't supported.

### Does it work in singleplayer?

Yes, out of the box. Multiplayer needs the **Paper plugin** — see
[[Multiplayer (Paper)]].

### If my mod is newer than the plugin (or vice-versa), does it still work?

It depends on the **protocol version**, not the release version. Both jars are
built from the same shared protocol code, which carries a `PROTOCOL_VERSION`
(currently **1**).

- **Same protocol version → it just works**, even if the display versions
  differ. Most updates (new tools, UI, fixes) don't change the wire format, so
  the protocol stays 1 and mixed nearby versions interoperate. You don't have to
  update both in lockstep.
- **Different protocol version → cleanly refused, not broken.** A newer mod
  against an older plugin gets an explicit handshake refusal in chat
  (*"Protocol mismatch (client v2, server v1) — update the mod or the
  plugin."*) and nothing is applied. It **fails safe**.

Check **Settings → the "Server:" row** to see the current link state. Update
both when release notes mention a protocol bump.

### Do other players need the mod to see my edits?

No. The server applies edits with authority and vanilla broadcasts the changes,
so everyone sees them. Only the **editor** needs the client mod (and the
`compbuild.edit` permission).

### Is it safe on a server with regions/claims?

With **WorldGuard** installed it respects region build permissions (blocks you
can't build are skipped and counted). Without a protection plugin, the
`compbuild.edit` permission is the only gate — grant it accordingly. See
[[Multiplayer (Paper)]].

### It says "networking failed to start" / "no plugin detected". What now?

Almost always a **stale client jar** or a plugin that didn't load. Follow the
**Troubleshooting the handshake** steps in [[Multiplayer (Paper)]] — the
in-game messages name the exact failing step.

### Can I edit with Air?

Yes — **Air** is the first entry in the material picker. Painting, filling, or
building with Air **erases**. See [[Materials, Palettes & Presets]].

### Are my settings saved?

Yes. Every tool's knobs, palettes, the material and recents, named palettes, and
presets are saved to `config/compbuildtools-settings.json` and restored next
launch.

### Is Studio Tools free?

Yes.

Studio Tools is free to use for personal and commercial Minecraft projects,
including public servers, commissions, content creation, and professional
builds.

There are no commercial licensing fees required to use Studio Tools.

See the repository's LICENSE file for details about permitted use and
redistribution.

### How do I report a bug?

Open an issue on the [repository](https://github.com/c0mputerrr/compbuildtools).
Include your Minecraft/mod versions, whether it's singleplayer or a Paper
server, and any relevant chat/console lines (the Settings "Server:" row and
"Font:" row are useful for those areas).

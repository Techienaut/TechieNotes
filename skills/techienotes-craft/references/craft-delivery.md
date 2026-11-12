# Craft delivery and verification

Read this before preparing native Craft payloads or publishing. The complete Markdown draft is the canonical delivery source; provider constraints cannot change its content or hierarchy. Use **Craft MCP or API only**, including verification; report checks the interface cannot perform.

## 1. Inspect the interface and destination

Discover available Craft tools and read their current help/schema. With the command connector, `blocks learn text code image concepts json limitations` is read-only; help for write commands may require the write tool. The representations below are compatibility guidance, subordinate to the live schema.

Resolve an existing destination link to the returned `rootBlockId`; its URL's document ID may differ. Modify only the requested content. When creation is requested, create one appropriately titled, emoji-prefixed document. Keep every generated block inline under its root; preserve hierarchy through indentation without child pages or page cards.

Check supported indentation, languages, media fields, and payload limits. Preserve the full draft when a limit prevents faithful delivery; report the specific limitation instead of clamping depth, flattening relationships, or dropping content. If Craft access is unavailable, return the complete Markdown artifact and state that it has not been published.

**Complete when:** the authorized destination and relevant schema limits are known, or the complete Markdown fallback and specific blocker are ready to return.

## 2. Build native blocks

Build an ordered array of sibling blocks under the document root. Use indentation for toggle children: nested `content` attached to a text block can convert it into a page.

| Content | Native representation |
| --- | --- |
| Heading | `type: "text"`, matching `textStyle: "h1"` through `"h4"`, `listStyle: "toggle"`, explicit `indentationLevel` |
| List item | `type: "text"`, appropriate bullet/numbered `listStyle`, explicit `indentationLevel` |
| Code block | `type: "code"`, exact `rawCode`, supported `language` when known, explicit `indentationLevel` |
| Image | Native image block with source URL, useful alt text, supported media metadata, and appropriate indentation |

Text `markdown` contains the emoji and heading number/content, without structural Markdown heading/list markers. Each two spaces of Markdown structural indentation becomes one native indentation level. Code's structural indentation belongs in metadata, never in `rawCode`; deliver code as a native code block, not fenced generic text.

Retain source language labels in the Markdown draft. Map equivalent provider identifiers only in native metadata, such as `sh` to `shell` when supported. Leave the code payload unchanged.

For images, use accurate metadata supported by the current schema. In one observed case, a remotely hosted SVG persisted with `mimeType: "image/svg+xml"`, `uploaded: false`, its URL, alt text, and indentation; a URL-only payload was silently omitted. Determine values from the actual media rather than copying that MIME type or upload status. A remote image is not an uploaded image, and a source link does not replace an instructional image.

**Complete when:** the entire payload maps to the draft in order, with faithful block types, hierarchy, code, and media metadata.

## 3. Preserve code through transport

Prefer structured tool arguments. Serialize JSON once with actual newline characters and original code whitespace. For command connectors that split semicolons or misparse apostrophes inside single-quoted JSON, encode those characters in the serialized JSON:

```javascript
const payload = JSON.stringify(blocks)
  .replace(/;/g, "\\u003B")
  .replace(/'/g, "\\u0027");
// Pass payload as the command's quoted JSON argument; JSON decoding restores it.
```

This encoding is connector-specific, not general shell quoting. Keep the sequences single-escaped in serialized JSON and actual line breaks in the data; avoid double-escaping or substituting literal `\\n` for newlines.

Use these comparisons during persistence checks:

- Compare every native `rawCode` directly with its source record, including tabs, nonbreaking spaces, blank lines, and trailing whitespace. Compare order as well as count.
- For inline code, compare the native text sliced by its code attributes against the source spans when available. Respect provider offset units; JavaScript slicing uses UTF-16 code units. Changed Markdown delimiters or escaping do not alone imply changed code.
- Inspect literal backticks and standalone backslashes when present. A standalone backslash previously required the padded double-backtick form below to survive Craft's parser. Use it only when needed, and verify the resulting native value before treating it as a repair.

```text
`` \ ``
```

If exact native inline-code comparison is unavailable, use another MCP/API-provided representation that establishes the rendered characters, or report exactness as unverified. Ambiguous serialized Markdown alone is insufficient evidence.

**Complete when:** transport preserves the prepared code data and the corresponding persistence comparisons are identified for every code item.

## 4. Write and recover

Finish the full draft and payload before the first destination write. Use one write if it fits; otherwise use ordered batches within current transport limits. Choose batch sizes from those limits, not from a past run.

Retain source records, payloads, source-to-block mapping, and confirmed block IDs/batches. Store full responses locally when useful; return compact counts and differences to the working context. One coordinator owns ordered destination mutations.

Check the first real batch's returned types/counts against its payload, then verify persistence for the types it introduced. Check images and unusual inline code as soon as they first occur. Use real content in source order, without throwaway documents or reordered test content. A success flag can conceal omitted image blocks.

After an error, timeout, or type/count mismatch, read the affected destination before retrying: a failed response can follow a committed write. Reconcile the confirmed prefix or individual missing blocks, then resume only known unwritten content. Stop dependent writes while written state is indeterminate. Repair only generated blocks with verified IDs and source-order anchors.

**Complete when:** all intended writes are reconciled to confirmed destination state, or dependent writes have stopped at a documented uncertainty with resumable records.

## 5. Verify persistence

Read back all generated content, exhausting every cursor on relevant reads, including nested content if returned. With the command connector, inspect both the outer `nextCursor` and the root node's `nextCursor`. Obtain fresh cursors after mutations.

Reconcile native block types, order, heading/list styles, indentation, text, code, image URLs, table-derived lists, quizzes, links, and absence of generated page cards against the payload and source mapping. Apply the code comparisons above. Check persisted images independently of the add response; success or a retained link does not prove image persistence.

After a complete baseline readback, a narrow repair requires fresh reads of changed IDs and affected ordering boundaries. Carry forward verified unchanged content. Repeat the full read only when structural changes or uncertain state invalidate the baseline. Derive final totals from persisted evidence.

**Complete when:** the complete baseline and any repairs reconcile to the intended content, or each remaining difference is explicitly identified.

## 6. Verify collapse and report

Set and verify **all generated toggle headings**, including nested headings, as collapsed through supported MCP/API controls. `listStyle: "toggle"` alone does not establish collapse state. If the interface cannot set or expose that state, report collapse as unverified; leave the Craft UI untouched.

Return the document link with the verification outcome and any material limitation. If publication is unavailable or incomplete, provide the complete Markdown artifact and identify precisely what remains unpublished or unverified. Correct only verified generated content within the request.

**Complete when:** the user has the deliverable and an accurate account of content persistence and collapse state.

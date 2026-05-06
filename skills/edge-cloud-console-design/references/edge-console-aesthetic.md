# Edge K3s Console Aesthetic

## North Star

The UI should feel like a local edge appliance control cockpit: compact, advanced, technical, and trustworthy. It is not a public cloud console and not a marketing page.

Users should feel: "this is the lightweight place where I can understand and control the k3s cluster running here."

## Visual Direction

Default to **frontier-tech operations**:

- Support both dark and light themes. The themes should feel like siblings, not two unrelated skins.
- Dark theme: dark technical shell, restrained luminous accents, strong telemetry contrast.
- Light theme: clean lab-console surface, high-contrast text, precise borders, subtle signal accents.
- Crisp surfaces with thin borders, not soft marketing cards.
- Subtle grid, signal, terminal, and telemetry cues.
- One primary signal accent, usually cyan or blue-green, supported by semantic green/amber/red.
- Use glow sparingly around active state or critical signal only.
- Avoid one-note purple/blue gradients, decorative blobs, glassmorphism, stock images, and feature-grid layout.
- In light theme, avoid full-page background grids. Keep grid/telemetry texture inside local maps, terminal panels, or diagnostic surfaces only.

Good words: local, edge, runtime, signal, telemetry, precise, compact, resilient, tactical.
Bad words: tenant, region, project, cloud account, marketplace, magical, stunning, all-in-one, effortless.

## Theme System

Always define themes with semantic tokens rather than one-off component colors.

Required token groups:

- Base: `bg`, `shell`, `surface`, `surface-2`, `surface-3`.
- Borders: `line`, `line-strong`, focus ring.
- Text: `text`, `muted`, `muted-2`, inverse text if needed.
- Signal: `accent`, `accent-2`, `accent-weak`.
- Status: ok/warn/bad/info foreground and weak backgrounds.
- Data: chart line, chart fill, table hover, progress track.
- Actions: primary, danger, disabled, overlay.

Dark theme guidance:

- Use deep blue-black or graphite foundations.
- Keep glows rare and low-opacity. Glow is for active state, focus, or critical runtime signal.
- Tables and panels should rely on borders and compact spacing, not big shadows.
- Ensure muted text remains readable on dark surfaces.

Light theme guidance:

- Use the feel of a modern observability console: pure white main canvas, light gray sidebar, white cards, thin neutral borders, quiet shadows, and a deep green/teal accent for active navigation and panel labels.
- Keep the same edge identity through monospace metadata, compact object tables, precise borders, and calm technical copy.
- Do not use a full-page grid background in light mode; it tends to read noisy and cheap. Use a plain background with crisp component borders.
- Avoid lab-grid wallpaper, SaaS-soft beige, warm gray, heavy drop shadows, and marketing-card composition.
- Status chips must remain readable without relying on color alone.

Implementation guidance:

- Prefer `:root` for dark defaults and `[data-theme="light"]` for light overrides, or equivalent framework theme providers.
- All components should consume tokens only. Avoid raw hex values inside component CSS except when declaring theme tokens.
- Add a theme switcher if the page is an interactive prototype or product shell.
- Verify both themes at desktop and mobile widths.

## Typography

The UI must optimize for scanning k3s objects and runtime facts.

- Use a legible UI sans for labels and Chinese text.
- Use tabular numbers for CPU, memory, disk, restart count, latency, pod count, and timestamps.
- Use monospace for node names, IPs, namespaces, image names, digests, endpoints, ports, commands, event IDs, and kubeconfig snippets.
- Keep headings compact. Console panels should not use hero-scale type.
- Avoid negative letter spacing and viewport-scaled font sizes.

Suggested hierarchy:

- Page title: 20-24px, semibold.
- Section title: 13-15px, semibold.
- Body/table text: 12-14px.
- Metadata: 11-12px.
- Metric values: 18-28px only for primary health/capacity signals.

## Layout Grammar

Common shell:

- Left nav: shallow local sections, active state visible.
- Top bar: cluster name, local endpoint, k3s version, sync state, global search, current session, logout.
- Main content: compact title, health summary, data surfaces, recent events, safe actions.
- No deep breadcrumb hierarchy. At most use one local context label like `本机集群`.
- Content width should use available space for tables and operational data.
- Spacing: 4px base grid; common steps 4, 8, 12, 16, 20, 24, 32.

First viewport priority:

1. Local cluster identity: name, endpoint, k3s version, sync time.
2. Health: API server, node readiness, pod health, pressure, warnings.
3. Inventory: nodes, pods, workloads, services, volumes.
4. Action: drain, cordon, restart, upgrade, backup, view logs, view YAML.

Required product shell:

- Login: focused centered auth card, clear product brand, username/password or token primary path, local endpoint as context, connection test, auth error state.
- Logout: explicit action visible in the shell; never hide logout only inside a menu for prototypes.
- Settings: local endpoint, kubeconfig/token, registry mirror, backup policy, upgrade channel, theme, diagnostics, certificate state.

Login page aesthetic:

- In light theme, use a plain light gray page background with a large white card, thin border, centered brand, strong title, restrained subtitle, generous input spacing, and a solid green primary button.
- Do not make login look like a settings form. Endpoint and kubeconfig details are supporting context, not the visual lead.
- Keep icons/links minimal and quiet. The login page should feel calm, direct, and product-grade.

## K3s Object Signals

Represent local k3s concepts explicitly:

- Cluster: name, local endpoint, k3s version, API server, container runtime, certificate age.
- Node: role, Ready/NotReady, internal IP, labels, taints, CPU/memory/disk pressure, pod capacity.
- Workload: namespace, kind, replicas, image, rollout state, restart count, update age.
- Pod: phase, node, restarts, QoS, age, containers, logs/exec/delete.
- Network: service, ingress, endpoint, CoreDNS, local gateway, port, certificate.
- Storage: PVC/PV, storage class, capacity, bound/pending, backup status.
- Events: severity, source, object, reason, message, timestamp.

## Component Standards

Tables:

- Must include search/filter, status, object name, namespace or node, runtime facts, and row actions.
- Prefer dense tables for k3s objects.
- Use status chips with label and severity, not color alone.
- Show timestamps as relative; exact time can be shown in title/tooltip when implemented.

Metrics:

- Pair values with thresholds or local meaning.
- Show pressure and capacity together, not isolated vanity numbers.
- Label units and windows.

Actions:

- `drain`, `cordon`, `delete`, `restart`, `upgrade`, `restore`, and token rotation are risk actions.
- Risk actions must show target scope, expected impact, and rollback path.

Events:

- Use monospace for reason IDs, object refs, and source names.
- Make warnings visually prominent but not noisy.
- Provide filters by severity, object type, namespace, and time window where possible.

## Chinese Console Copy Guidance

Keep wording short, operational, and local:

- Prefer: `本机集群`, `节点`, `工作负载`, `Pod`, `服务`, `Ingress`, `存储卷`, `事件`, `镜像`, `备份`, `升级`, `排空`, `暂停调度`, `恢复调度`, `查看日志`, `查看 YAML`.
- Avoid: `租户`, `地域`, `项目`, `云账号`, `可用区`, `开通`, `订购`, `一站式`, `赋能`.
- Empty states should distinguish "healthy empty" from "not configured" or "collector unavailable".

## Review Checklist

Before accepting a generated UI, ask:

- Does it avoid public-cloud hierarchy entirely?
- Does the first viewport show the local cluster identity and health?
- Are k3s objects represented concretely, not replaced by generic "resources"?
- Is the style advanced and technical without hiding data?
- Are risky local operations scoped and confirmable?
- Are loading, empty, error, degraded, and permission states designed?
- Would the UI still work if the decorative grid/glow was removed?

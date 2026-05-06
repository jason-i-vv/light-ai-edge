---
name: edge-cloud-console-design
description: Design or review frontends for a lightweight edge k3s cluster management console. Use when building local k3s UI pages, dashboards, node/workload/network/storage/event views, design systems, visual QA, or frontend prompts where the result must combine frontier-tech aesthetics with a flat, practical edge cluster management structure rather than public-cloud tenant/region hierarchy.
---

# Edge Cloud Console Design

## Operating Thesis

This product is a **local edge k3s cluster console**, not a public cloud console. Do not introduce tenants, regions, projects, availability zones, billing hierarchy, or cloud-resource nesting unless the product explicitly adds those concepts.

The desired feel is **frontier-tech operations**: advanced, precise, compact, system-like, and visually distinctive. The UI should look like a serious edge device / k3s control cockpit for local operators and developers, not a generic SaaS dashboard.

## Core Goals

1. **Aesthetic system:** Make generated pages feel like a modern edge technology product in both light and dark themes: crisp data surfaces, subtle grid/terminal cues, sharp status language, technical typography, restrained signal accents, and purposeful contrast.
2. **Engineering structure:** Keep the product model flat and useful for a lightweight k3s manager: login/session, overview, nodes, workloads, pods, services/ingress, storage, images, events, settings, upgrade, backup, logout, and local access.

## When Triggered

Use this skill for:
- Local k3s cluster overview, node, workload, pod, service, ingress, storage, image, event, setting, backup, upgrade, and troubleshooting pages.
- Frontend component generation for this edge console.
- Design-system or `DESIGN.md` work for the console.
- Visual QA when pages feel like public-cloud clones, marketing pages, or random AI dashboards.

Do not use this skill for public cloud consoles, marketing landing pages, multi-tenant admin portals, or billing/account-management systems unless the user explicitly changes the product scope.

## Workflow

1. **Classify the screen.** Pick one: local overview, nodes, workloads, pods, service/network, storage, images, events/logs, settings, upgrade/backup, or troubleshoot.
2. **Name the local operator task.** What does the user need in the first 5 seconds? Examples: "is this k3s healthy?", "which node is saturated?", "which workload failed?", "can I safely drain this node?"
3. **Reject cloud hierarchy.** Remove tenant/project/region/zone language. Use local scope: cluster name, node, namespace, workload, service, image, volume, event, endpoint, token, backup.
4. **Load the aesthetic reference.** Read `references/edge-console-aesthetic.md` before substantial UI creation or review.
5. **Design the operational structure first.** Prioritize health, capacity, runtime state, recent events, and safe actions.
6. **Define theme tokens.** Create light and dark theme variables before component styling. Use semantic tokens for background, shell, surface, border, text, muted text, accent, statuses, charts, focus, and risk actions.
7. **Apply frontier-tech styling second.** The style should amplify the product identity without hiding data or making controls feel decorative.
8. **Verify visually.** Check desktop and mobile screenshots in both themes when implementing. Confirm the first viewport is a real local cluster console, not a marketing hero.

## Product Structure Defaults

Keep navigation shallow:

- **总览:** cluster health, k3s version, API server status, node readiness, pod health, resource pressure, recent events, quick actions.
- **节点:** node list, role, status, internal IP, CPU/memory/disk pressure, pod allocation, labels, drain/cordon/reboot actions.
- **工作负载:** namespace, deployment/statefulset/daemonset/job, replicas, image, restart count, rollout status, YAML/log actions.
- **Pods:** phase, node, restarts, age, QoS, image, logs, exec, delete.
- **服务网络:** service, ingress, endpoint, port, CoreDNS, local gateway, certificate.
- **存储:** PV/PVC, storage class, capacity, mount status, backup status.
- **事件:** warning/normal events, source, object, message, timestamp, correlation ID when available.
- **登录:** local password/token/kubeconfig entry, connection test, offline/error state, "remember this device" only if the product supports it.
- **会话/注销:** current user/session source, token age, permission level, explicit logout, session-expired state.
- **设置:** local endpoint, kubeconfig, access token, registry mirror, upgrade channel, backup policy, theme preference, diagnostics collection, TLS/certificate state.

## Aesthetic Rules

- Provide both **亮色主题** and **暗色主题** unless the user explicitly asks for one theme only.
- Dark theme should feel like an edge operations cockpit: dark technical shell, luminous but restrained signal accents, and high legibility for telemetry.
- Light theme should feel like a lab-grade technical console: clean high-contrast neutral surfaces, crisp grid/border discipline, and the same frontier-tech identity without becoming a public-cloud admin template.
- Use cyan/blue-green/lime accents sparingly for signals, not decoration.
- Use subtle grid lines, scanline-like separators, compact panels, terminal-style metadata, and precise status markers when they support the "edge tech" theme.
- Use monospaced text for node names, IPs, images, digests, ports, commands, namespaces, and event IDs.
- Keep page titles compact. No hero-scale headings inside the console.
- Use tables and dense lists for k3s objects. Use cards only for health/capacity summaries and framed tools.
- Avoid rounded, soft SaaS dashboard styling. Radius should usually be 4-8px.
- Every decorative treatment must serve one of: scope, state, grouping, risk, or system identity.

## Hard Rules

- No tenant, region, project, availability-zone, billing, marketplace, or cloud-account concepts.
- No public-cloud breadcrumb stacks like `Cloud / Container / Cluster`.
- No marketing copy, feature grids, giant welcome banners, or centered hero sections.
- The first viewport must show local cluster identity, health, nodes/workloads, and recent events.
- The product shell must include login, logout, and settings structure even when the page prototype uses simulated data.
- Risky actions such as drain, delete, upgrade, restart, token rotation, and backup restore must show scope and confirmation.
- Empty states must say whether the local cluster is healthy-empty or missing configuration.
- Mobile must prioritize health, node state, warnings, and safe approval/retry actions.

## Output Expectations

When designing or reviewing, include:

- Screen type and local operator task.
- Flat information hierarchy for the first viewport.
- Which k3s objects are represented.
- Aesthetic decisions that create frontier-tech identity.
- Light/dark theme token decisions, including contrast and status-color behavior in both themes.
- State coverage: loading, empty, error, degraded, permission, long-running, partial success, destructive confirmation.
- Anti-cloud pass: what tenant/region/project/public-cloud patterns were removed or avoided.
- Anti-slop pass: what generic AI-dashboard patterns were removed or avoided.

## Review Scorecard

Rate 0-10 and fix anything below 8:

- Local k3s fit: does it avoid public-cloud hierarchy?
- Frontier-tech aesthetic: does it feel like a distinctive edge product?
- Operational hierarchy: can users see health and risk quickly?
- Engineering structure: are nodes, workloads, pods, services, storage, events, and settings arranged coherently?
- Density and scanability: can users compare objects without noise?
- State and risk coverage: are failures and destructive actions designed?
- AI slop resistance: would this pass as intentionally designed rather than template-generated?

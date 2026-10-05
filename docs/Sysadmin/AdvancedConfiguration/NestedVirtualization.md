# Nested Virtualization

Nested virtualization (running a hypervisor inside a VM, e.g. KVM with the Intel `vmx` / AMD `svm`
CPU feature) is now **opt-in** in G8. Every VM carries its own `allow_nesting` flag which is rendered
into the VM's libvirt XML at boot:

- flag **off** → the `vmx` and `svm` CPU features are explicitly disabled in the guest
- flag **on** → the features are left to the `host-model` CPU mode, which enables them on
  nested-capable hosts

Because the feature is applied at boot, it only takes effect on the VM's **next start/reboot**.

Configuration key: `allow_nesting_virtualization`
Configuration value: `true` / `false`
Location: [`environment.settings`](../../Installation/System-config.md#environment)

## Default values

Default is `false`. If the key is missing it is treated as `false`.

## Behaviour

`allow_nesting_virtualization` is a grid-level switch that controls whether administrators are
allowed to **enable** nested virtualization on a VM through the API.

- When the setting is `false`, the API refuses to enable nesting on any VM that does not already
  have it enabled. Disabling nesting is always allowed, and VMs that already have it on are
  unaffected.
- When the setting is `true`, nesting can be enabled on any (halted) VM.

This setting does not change the per-VM flag itself; it only gates whether a VM whose nesting is
currently **off** may be switched **on**.

## Per-VM API

Nested virtualization is managed per VM with the following endpoints (VM must be `HALTED`):

- `POST /api/1/virtual-machines/<vm_id>/nesting` — enable
- `DELETE /api/1/virtual-machines/<vm_id>/nesting` — disable

Both return an error when the VM is not halted, and enabling additionally returns an error when the
grid `allow_nesting_virtualization` setting is `false` and the VM does not already have nesting
enabled. The current value is exposed on the VM list and VM details as `allow_nesting`.

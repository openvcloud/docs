# Image actions

## Disabling Image

Active images in status CREATED on can be disabled by calling administrative action `disable`:

* Disabling image consists of setting in the image model:
  * status to DISABLED;
  * flag `enabled` to `False`.

Disabled images cannot be used for creating new VMs.
Actions allowed on disabled CSs (and all CS resourses):

* for users of `admin` group and users with `write` rights on account: `enable`, `delete`** image.
* for other users: no actions allowed.

** Note that system images cannot be deleted.

## Enabling Image

Disabled images can be enabled by calling administrative action `enable`:

* Enabling image consists of setting in the image model:
  * status to ENABLED;
  * flag `enabled` to `True`.

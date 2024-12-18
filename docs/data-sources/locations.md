---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "hcloud_locations Data Source - hcloud"
subcategory: ""
description: |-
  Provides a list of available Hetzner Cloud Locations.
  This resource may be useful to create highly available infrastructure, distributed across several locations.
---

# hcloud_locations (Data Source)

Provides a list of available Hetzner Cloud Locations.

This resource may be useful to create highly available infrastructure, distributed across several locations.

## Example Usage

```terraform
data "hcloud_locations" "all" {}

resource "hcloud_server" "workers" {
  count = 5

  name        = "node${count.index}"
  image       = "debian-12"
  server_type = "cx22"
  location    = element(data.hcloud_locations.all.locations, count.index).name
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Read-Only

- `descriptions` (List of String, Deprecated)
- `id` (String) The ID of this resource.
- `location_ids` (List of String, Deprecated)
- `locations` (Attributes List) (see [below for nested schema](#nestedatt--locations))
- `names` (List of String, Deprecated)

<a id="nestedatt--locations"></a>
### Nested Schema for `locations`

Read-Only:

- `city` (String) Name of the closest city to the Location. City name and optionally state in short form.
- `country` (String) Country the Location resides in. ISO 3166-1 alpha-2 code of the country.
- `description` (String) Description of the Location.
- `id` (Number) ID of the Location.
- `latitude` (Number) Latitude of the city closest to the Location.
- `longitude` (Number) Longitude of the city closest to the Location.
- `name` (String) Name of the Location.
- `network_zone` (String) Name of the Network Zone this Location resides in.

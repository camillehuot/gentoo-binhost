# gentoo-binhost

Portage configuration for a Gentoo binhost.

## Quickstart

`world` and `etc_portage` are in Git, they can be modified.

`mkdir repos_gentoo binpkgs home` to create the rest from scratch.

```sh
podman run --rm -it --name binhost --privileged \
	-v $(pwd)/world:/var/lib/portage/world \
	-v $(pwd)/etc_portage:/etc/portage \
	-v $(pwd)/repos_gentoo:/var/db/repos/gentoo \
	-v $(pwd)/binpkgs:/var/cache/binpkgs \
	-v $(pwd)/home:/root \
       	gentoo/stage3 bash

```

## Initialise the Portage

`emerge --sync`

## Build the packages

`emerge -DuN @world`

## Start the local binhost

`python -m http.server`

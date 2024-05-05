# docker-librarian-quay

A [Librarian](https://codeberg.org/librarian/librarian/) image, on Quay.

[Quay page](https://quay.io/repository/pussthecatorg/librarian) | [GitHub page](https://github.com/PussTheCat-org/docker-librarian-quay)

This image mostly exist for the [PussTheCat.org](https://pussthecat.org/) [instance](https://librarian.pussthecat.org/), but others are free to use it.

This image was made because, even though the project is deprecated, it still works. However, since the project was archived so "fresh" image was built, which mean that the upstream image is potentially vulnerable. This image is just a drop in replacement for the upstream image.


## Usage:

- Download (or copy the content of) the `docker-compose.yml` 
- Download (or copy the content of) the `config.yml` from this repository, or from upstream: https://codeberg.org/librarian/librarian/src/branch/main/config.example.yml
- Customize the `config.yml` file how you want 

    Note:

    - deployment/host must be set to 0.0.0.0

    - uncomment every functions under cache and set url to `"redis://librarian-redis:6379"` to use Redis

- Move both files to the folder you want
- `docker-compose up -d`

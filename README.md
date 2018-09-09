## React Image Gallery 8.x-1.x

### About this Module

This module provides a dynamic Image Gallery based on the React Image Gallery component.
(https://github.com/xiaolin/react-image-gallery).

The idea of the module came during investigating ways to develop React components under Drupal.

### Goals

* A simple way to display an Image Gallery on any Drupal 8 website
* Have few dependencies on 3rd parties
* Flexibity for the site builders

### Requirements

Module depends on Media (core) and Paragraphs module.

* TODO replace old Paragraphs solution with layout sections

### Installation

* Install as you would normally install a contributed Drupal module.
  See: https://www.drupal.org/node/895232 for further information.

### Configuration

1.  Enable the 'React Image Gallery' module and desired sub-modules in 'Extend'. (/admin/modules)

2.  Configure a content type (or a custom block) with an entity reference revisions (Paragraph)

3.  Create some gallery media items. (/media/add/gallery_image)

4.  Create or edit a content of the type configured on step 4 and add a 'Image Gallery' paragraph.

5.  Configure the paragraph with the media items you want.

6.  Save the content and confirm that the 'React Image Gallery' is loaded in the page.

### Development on the react App

The react app resides in the js directory (/react_image_gallery/js), to build or make changes its required to run:

```
yarn install
```

then the app can built:

```
yarn build
```

to start the app:

```
yarn start
```

When running the app locally it's required to mock in the js/public/index.html the settings that are passed to the gallery component,
those settings shall reflect the paragraph id where the gallery is present in Drupal:

```
var drupalSettings = {
  gallery: {
    1: {
      id: '<PARAGRAPH_ENTITY_ID>',
      element: 'react-image-gallery-block',
      settings: {
        'infinite': true,
        'lazyLoad': true,
        'showNav': true,
        'showThumbnails': true,
        'showFullscreenButton': true,
        'showPlayButton': true,
        'showBullets': false,
        'showIndex': false,
        'autoPlay': false
      }
    }
  }
};
```

Its also required to enable CORS settings in Drupal, add the below lines inside parameters attribute to your development.services.yml:

```
cors.config:
  enabled: true
  # Specify allowed headers, like 'x-allowed-header'.
  allowedHeaders: ['x-csrf-token', 'authorization', 'content-type', 'accept', 'origin', 'x-requested-with']
  # Specify allowed request methods, specify ['*'] to allow all possible ones.
  allowedMethods: ['POST', 'GET', 'OPTIONS']
  # Configure requests allowed from specific origins.
  allowedOrigins: ['*']
  # Sets the Access-Control-Expose-Headers header.
  exposedHeaders: true
  # Sets the Access-Control-Max-Age header.
  maxAge: false
  # Sets the Access-Control-Allow-Credentials header.
  supportsCredentials: false
```

### Author/Maintainer

* Paulo Gomes (pauloamgomes) - https://www.drupal.org/u/pauloamgomes

* Fork author under(de)construction ChS - https://www.drupal.org/u/chs

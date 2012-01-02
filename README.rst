Introduction
============

This addon register the jquery plugin oembed_ in the Plone resource registry.

Version: 1.1.0 RC

How to use jquery.oembed
========================

Explicit example::

    <script type="text/javascript">
    $(document).ready(function() {
            $("#container").oembed("http://www.flickr.com/photos/14516334@N00/345009210/");
    });
    </script>
    <div id="container"></div>

Implicit example::

    <script type="text/javascript">
            $(document).ready(function() {
                    $("a.oembed").oembed();
            });
    </script>
    <div><a href="http://www.flickr.com/photos/14516334@N00/345009210/" class="oembed">Flickr Image</a></div>
    <div><a href="http://vimeo.com/3108686" class="oembed">Vimeo Video</a></div>

Configuring multiple providers example
--------------------------------------

::

    <script type="text/javascript">
            $(document).ready(function() {
                    $(".oembed").oembed(null, 
                            {
                            embedMethod: "append", 
                            maxWidth: 1024,
                            maxHeight: 768,
                            vimeo: { autoplay: true, maxWidth: 200, maxHeight: 200}                 
                            });
            });
    </script>
    <div><a href="http://vimeo.com/3108686" class="oembed">Vimeo Video</a></div>
    <div><a href="http://www.flickr.com/photos/14516334@N00/345009210/" class="oembed">Flickr Image</a></div>

Supported OEmbed providers
--------------------------

* 5min
* Amazon Product Images
* Flickr
* Google Video
* Hulu
* Imdb
* Metacafe
* Myspace Videos
* Qik
* Revision3
* Screenr
* Slideshare
* Twitpic
* Viddler
* vVimeo
* Wikipedia
* WordPress
* YouTube

This javascript plugin relays in 'jsonp', so only oEmbed providers that support
callback methods are directly implemented.

Any other oEmbed provider uses embedly_ service.

How to manage providers
-----------------------

'greedy' option let you activate a fallback service to not natively supported
services, by default the service used is oohembed_.

allowed providers::

    $(".oembed").oembed(null, { allowedProviders: ["flickr", "youtube"] });

custom providers::

        $(".oembed").oembed(null, {
            greedy: false,
            customProviders: [{
                "name": "streetfire.net",
                "urlschemes": ["streetfire\\.net\/video\/.*"],
                "apiendpoint": "http://api.embed.ly/v1/api/oembed?"
            }]
        });

disallowed providers::

    $(".oembed").oembed(null, { disallowedProviders: ["flickr", "youtube"] });

default oembed provider::

    $(".oembed").oembed(null, {defaultOEmbedProvider: "embed.ly"});

embeded method
--------------

append::

    $(".oembed").oembed(null, {embedMethod: "append"});

It append to the .oembed container the result with a container classified::

    <a href="..." class="oembed">...</a>
    <div class="oembed-container oembed-container-Vimeo">...</div>

fill::

    $(".oembed").oembed(null, {embedMethod: "fill"});

It fill the link with the results::

    <a href="..." class="oembed">
      <div>...</div>
    </a>

replace::

    $(".oembed").oembed(null, {embedMethod: "replace"});


It replaces the link with the html snippet

manage size
-----------

You can add a size constraint to the html snippet. You can set maxWidth and/or
maxHeight::

    $(".oembed").oembed(null, { 
            maxWidth: 400, 
            maxHeight: 300 });
    });



Credits
=======

Companies
---------

|makinacom|_

  * `Planet Makina Corpus <http://www.makina-corpus.org>`_
  * `Contact us <mailto:python@makina-corpus.org>`_


Authors

  - JeanMichel FRANCOIS aka toutpt <toutpt@gmail.com>

Contributors

  - Johannes Raggam <raggam-nl@adm.at>

.. |makinacom| image:: http://depot.makina-corpus.org/public/logo.gif
.. _makinacom:  http://www.makina-corpus.com
.. _oembed: https://code.google.com/p/jquery-oembed
.. _embedly: http://embed.ly
.. _oohembed: www.oohembed.com

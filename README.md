Commons Gender Bundle
=====================

Since [gender is not binary][1] but Symfony documentation and tutorials and popular
bundles play as if it were, this bundle attempts to be a starting point for Symfony
web applications to offer humane choices for users to identify themselves.

[1]: http://geekfeminism.wikia.com/wiki/Gender_and_sex#Gender

Installation
------------

Add the following code to your ```composer.json``` file:

    "require": {
        ..
        "commons/gender-bundle": "dev-master"
    },

And then run the Composer update command:

    $ php composer.phar update commons/gender-bundle

Then register the bundle in the `AppKernel.php` file:

    public function registerBundles()
    {
        $bundles = array(
            ...
            new Commons\Bundle\GenderBundle\CommonsGenderBundle(),
            ...
        );

        return $bundles;
    }

Configuration
-------------

Configuration is required for this bundle to function. Add the gender options your
application supports to your `config.yml`

```yml
commons_gender:
    genders:
        f: Feminine
        m: Masculine
        q: Genderqueer
        u: Undisclosed
```

These are the choices that will be available in the `gender` form type.

The `gender` form type extends from [Symfony's `choice` form type][2], which means it
supports `multiple`. However it is your responsibility to create a data model that
supports multiple genders.

[2]: http://symfony.com/doc/current/reference/forms/types/choice.html

Interfaces
----------

This bundle provides a generic `GenderedUserInterface` that all other gendered user
interfaces should extend from. The `GenderedUserInterface` tries to make no assumptions
and so only defines a `GENDER_UNKNOWN` constant.

Ambitions
---------

The maintainers of this bundle will likely create a `freegender` form type which allows
free input with optional autocompletion.

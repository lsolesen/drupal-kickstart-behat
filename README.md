drupal-kickstart-behat
======================

Modified from the proof of concept for a session at Drupalcamp London (http://2013.drupalcamplondon.co.uk/session/zip-bdd-do-dah-zip-bdd-ay).

Uses the Drupal 7 Commerce Kickstart profile (http://drupal.org/project/commerce_kickstart),
with Behat/Mink testing using Travis CI (https://travis-ci.org) and Selenium.


[![Build Status](https://travis-ci.org/lsolesen/drupal-kickstart-behat.png?branch=master)](https://travis-ci.org/lsolesen/drupal-kickstart-behat)

## Installation

    # Clone repo
    git clone https://github.com/lsolesen/drupal-kickstart-behat.git public_html

    # Create Drupal codebase
    cd public_html
    drush make build-commerce-kickstart.make www

    # Install Drupal
    cd www
    drush si commerce_kickstart --sites-subdir=default --db-url=mysql://USERNAME:PASSWORD@localhost/DB_NAME --account-name=admin --account-pass=admin --site-mail=admin@example.com --site-name="Commerce Kickstart Profile" --yes
    # Install testing tools
    cd ../../tests/behat
    curl -s http://getcomposer.org/installer | php
    php composer.phar install

##### Configure Behat
Modify `/tests/behat/behat.yml`
Set `base_url` to your local host

Edit `behat.local.yml` and set your drush alias for the site you are testing.

To run tests

    # Run tests
    cd /tests/behat
    ./bin/behat

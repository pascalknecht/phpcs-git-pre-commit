# PHPCS git pre-commit hook

## About

Auto installed git pre-commit hook for running [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer) 
code checking to PSR2 coding standard compliance. It checks only files that are to be committed.

Inspired by [Enforce code standards with composer, git hooks, and phpcs](http://tech.zumba.com/2014/04/14/control-code-quality/)

## Installation

Install `pascalknecht/phpcs-git-pre-commit` via composer.json File

     "repositories": [
        { "type": "composer", "url": "https://wpackagist.org" },
        {
            "type": "vcs",
            "url": "https://github.com/pascalknecht/phpcs-git-pre-commit"
        }
    ],
    "require-dev": {
        "pascalknecht/phpcs-git-pre-commit": "dev-master"
    },

To enable code sniff, аdd to `post-install-cmd` and `post-update-cmd` in `composer.json` installation script:

    "post-install-cmd": [
        "sh ./vendor/pascalknecht/phpcs-git-pre-commit/src/setup.sh"
    ],
    "post-update-cmd": [
        "sh ./vendor/pascalknecht/phpcs-git-pre-commit/src/setup.sh"
    ]

Then run `composer install` or `composer update`. `pre-commit` hook will be installed or updated if it already exists.

## Usage

Run `git commit` and pre-commit hook will check your committed files like if you run

    php phpcs.phar --standard=PSR2 --encoding=utf-8 -n -p /path/to/file.php

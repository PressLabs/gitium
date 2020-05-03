Gitium [![Build Status](https://travis-ci.org/PressLabs/gitium.svg)](https://travis-ci.org/PressLabs/gitium) [![Coverage](https://codeclimate.com/github/PressLabs/gitium/coverage.png)](https://codeclimate.com/github/PressLabs/gitium) [![Code Climate](https://codeclimate.com/github/PressLabs/gitium.png)](https://codeclimate.com/github/PressLabs/gitium)
======

# Welcome to Gitium

Gitium was built in 2013 to provide our clients a more simple and error-free method to integrate a new git version control into their code management flow.

Gitium was developed by the awesome engineering team at [Presslabs](https://www.presslabs.com/), a Managed WordPress Hosting provider.

For more open-source projects, check [Presslabs Code](https://www.presslabs.org/). 

### What is Gitium?

This plugin enables continuous deployment for WordPress, integrating with tools such as Github, Bitbucket or Travis-CI. Theme or plugin updates, installs and removals are all automatically versioned. Ninja code edits from the WordPress editor are also tracked by the version control system.

### Why Gitium?

Gitium is designed with responsible development environments in mind, allowing staging and production to follow different branches of the same repository. You can also deploy code by simply using git push.

Gitium requires git command line tool with a minimum version of 1.7 installed on the server and the proc_open PHP function enabled.

### Gitium features:

- preserves the WordPress behavior
- accountability for code changes
- safe code storage—gets all code edits in Git

### Development

For more details about Gitium, head here: https://www.presslabs.org/gitium/docs/usage/

### Working with Heroku / Dokku

We recommend using a separate 'gitium' branch for automatic pushes from Gitium.

Add a composer.json file to your root source folder, to save the original .gitignore that would otherwise be deleted by herokuish as
part of deployment:
```
{
    "scripts": {
        "post-install-cmd": [
            "cp .gitignore .gitignore_gitium"
        ]
    }
}
```

Modify your .gitignore, to have at least the following lines:
```
*.log
*.swp
*.back
*.bak
*.sql
*.sql.gz
~*
.maintenance
wp-content/blogs.dir/
wp-content/upgrade/
wp-content/backup-db/
wp-content/cache/
wp-content/backups/
wp-content/uploads/
secret/
**/node_modules/
!wp-content/**/vendor/

.heroku/
.profile.d/
vendor/
.composer/
.builders_run
.bash_history
.rnd
.release
.env
*log.txt
```

Add this to your wp_config.php:
```
define( 'GITIUM_REMOTE_URL', <YOUR_REPO_URL>);
define( 'GITIUM_REMOTE_TRACKING_BRANCH', 'gitium' );
```

The deployment process would consist of:

1) Merge contents of 'gitium' branch into 'master', making sure merged contents are correct.

2) Deploy with ```git push dokku``` as usual.


### Contributing

We’ve built this to make our lives easier and we’re happy to do that for other developers, too. We’d really appreciate it if you could contribute with code, tests, documentation or just share your experience with Gitium.

Development of Gitium happens at http://github.com/PressLabs/gitium 
Issues are tracked at http://github.com/PressLabs/gitium/issues 
This WordPress plugin can be found at https://wordpress.org/plugins/gitium/

### License

This project is licensed under the [General Public License version 2.0](http://www.gnu.org/licenses/gpl-2.0.html).


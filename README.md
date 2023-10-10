# Senior Wordpress Developer Assessment

WordPress Plugin: "Was this article Helpful?"

## Task Overview
In this task, your objective is to develop a OOP WordPress plugin that allows website visitors to vote on various articles. Your goal is to create a user-friendly, efficient, and secure plugin that integrates seamlessly with WordPress websites.

Please read carefully the full requirements, before stating the development.

With this project you can quickly run the following:

- [WordPress and WP CLI](https://hub.docker.com/_/wordpress/)
- [phpMyAdmin](https://hub.docker.com/r/phpmyadmin/phpmyadmin/)
- [MySQL](https://hub.docker.com/_/mysql/)

## Contents

- [Requirements](#requirements)
- [Configuration](#configuration)
- [Installation](#installation)
- [Usage](#usage)
- [Plugin Requirements](#plugin-requirements)
- [Plugin description and functionality](#1.-plugin-description-and-functionality)
- [Admin Functionality](#2.-admin-Functionality)
- [Front-End](#3.-front-end)
- [4. Security](#4.-security)
- [5. Caching](#5.-caching)
- [6. Documentation](#6.-documentation)
- [7. Testing](#7.-testing)
- [8. Submission](#8.-submission)
- [9. Timeline](#9.-timeline)
- [Side Notes](#side-notes)

## Requirements

Make sure you have the latest versions of **Docker** and **Docker Compose** installed on your machine.

Clone this repository or copy the files from this repository into a new folder. In the **docker-compose.yml** file you may change the IP address (in case you run multiple containers) or the database from MySQL to MariaDB.

Make sure to [add your user to the `docker` group](https://docs.docker.com/install/linux/linux-postinstall/#manage-docker-as-a-non-root-user) when using Linux.

## Configuration

Copy the example environment into `.env`

```
cp env.example .env
```

Edit the `.env` file to change the default IP address, MySQL root password and WordPress database name.

## Installation

Open a terminal and `cd` to the folder in which `docker-compose.yml` is saved and run:

```
docker-compose up
```

This creates two new folders next to your `docker-compose.yml` file.

* `wp-data` – used to store and restore database dumps
* `wp-app` – the location of your WordPress application

The containers are now built and running. You should be able to access the WordPress installation with the configured IP in the browser address. By default it is `http://127.0.0.1`.

For convenience you may add a new entry into your hosts file.

## Usage

### Starting containers

You can start the containers with the `up` command in daemon mode (by adding `-d` as an argument) or by using the `start` command:

```
docker-compose start
```

### phpMyAdmin

You can also visit `http://127.0.0.1:8080` to access phpMyAdmin after starting the containers.

The default username is `root`, and the password is the same as supplied in the `.env` file.

---

# Plugin Requirements

## 1. Plugin description and functionality
Implement a simple voting system with two actions (buttons) - Yes and No. Each one will add a “Positive” or “Negative” count to the voting results. Show the voting results as an average percentage. Use an Ajax request, to submit the user vote.
Once, the user votes, he will be able to see the voting results in average percentage and the buttons will remain inactive, but also will show your vote (even if you refresh the page).
User fingerprint protection: Implement IP-based protection (or similar) to prevent multiple votes from the same IP. Also, clear the collected fingerprints after X number of votes.
Responsive Design: Ensure that the voting elements are responsive and work well on various devices and screen sizes.
Shortcode Support: Enable users to add the voting elements to posts, pages, and custom post types using shortcode.
Structure: Full-OOP, without using boilerplate templates, try to establish your own infrastructure, that is friendly and intuitive, following the WordPress coding standards.

## 2. Admin Functionality
Post Edit: When we edit an article, we should be able to see the voting results, as shown below, using a side meta widget:

Edit Votes: This one is optional. If you want to gain some extra points on the task, please add the possibility to edit the votes within the admin meta widget.

## 3. Front-End
For the front-end, you need to include webpack with sass. Use variables to set the main blue accent color.
For the icons, please generate a font. You can use the IcoMoon App. Similar SVG icons can be found on the Google Material Symbols and Icons Set.
Below, you can see the design that you should aim to achieve on the front-end:


## 4. Security
Sanitization: Sanitize user inputs to prevent SQL injection and cross-site scripting.
Validation: Validate user inputs to ensure data integrity.
Permissions: Implement appropriate permission checks to restrict access to plugin settings and voting functionality.
Hashing: Use a one-way encryption/hashing method to store the user sensitive information, like the IP.

## 5. Caching
Let's consider that we are implementing this feature on a website, that is using Cloudflare, and the whole page is being cached. So, make sure that you are always showing a relevant content to the end-user. How would you do that?
Imaging, that you can use a method to purge the Cloudflare cache, like:

```
/**
 * Purge the cache of a post, by it\'s post_id
 *
 * @param int $post_id The Post ID.
 */

cloudflare_purge_cache( $post_id );
```

## 6. Documentation
User Guide: Create comprehensive documentation for users on how to install, configure, and use the plugin.
Code Comments: Provide clear and well-documented code with inline comments to explain the functionality and logic.

## 7. Testing
Functional Testing: Thoroughly test the plugin's functionality to ensure it works as expected.
Compatibility Testing: Ensure compatibility with the latest WordPress version and basic WordPress themes.
Security Testing: Perform security testing to identify and fix any vulnerabilities.

## 8. Submission
Code Repository: Once you get access to our evaluation repository, please create a PR with your work.

## 9. Timeline
You will have [insert timeline] to complete this task. Please let us know if you need extra time to complete.

Evaluation Criteria:
Code quality and organization.
User-friendliness and design of the user interface.
Security measures and data protection.
Compliance with WordPress coding standards.
Documentation quality.
Responsiveness and performance.
Successful completion of all specified features and requirements.

## Side Notes
* During the interview, you may be asked to explain your design decisions, showcase the plugin's functionality, and demonstrate your coding skills.
* If you are having any troubles with the project installation, please use your own repository with the base plugin source.

Good luck!

SMF and MediaWiki Integration
=============================
Author: live627 (live627 at gmail dot com)
Author: SleePy (sleepy at simplemachines dot org)
Original Author: Ryan Wagoner (rswagoner at gmail dot com)
Version: 1.13

Place this file in your wiki/extenstions folder. If you
encouter an issue be sure to read the known issues below.

Add to LocalSettings.php
========================
```
# This requires a user be logged into the wiki to make changes.
$wgGroupPermissions['*']['edit'] = false; // MediaWiki Setting

# If you experience the issue where you appear to be logged in
# eventhough you are logged out then disable the page cache.
#$wgEnableParserCache = false;
#$wgCachePages = false;

# SMF Authentication
# To get started you only need to configure wgSMFPath.
# The rest of the settings are optional for advanced features.

# Relative path to the forum directory from the wiki
# Do not put a trailing /
# Example: /public_html/forum and /public_html/wiki -> ../forum
$wgSMFPath = "../forum";

# Use SMF's login system to automatically log you in/out of the wiki
# This works best if you are using SMF database sessions (default).
# Make sure "Use database driven sessions" is checked in the
# SMF Admin -> Server Settings -> Feature Configuration section
# NOTE: Make sure to configure the wgCookeDomain below
#$wgSMFLogin = true;

# Members in these SMF groups will not be allowed to sign into wiki.
# This is useful for denying access to wiki and a easy anti-spam
# method.  The group ID, which can be found in the url (;group=XXX)
# when viewing the group from the administrator control panel.
#$wgSMFDenyGroupID = array(4);

# Grant members of this SMF group(s) access to the wiki
# NOTE: The wgSMFDenyGroupID group supersedes this.
#wgSMFGroupID = array(2);

# Grant members of this SMF group(s) wiki sysop privileges
# NOTE: These members must be able to login to the wiki
#$wgSMFAdminGroupID = array(1, 3);

# SMF to wiki group translation.  This allows us to assign wiki groups
# to those in certain SMF groups.
#$wgSMFSpecialGroups = array(
#	// SMF Group ID => Wiki group name.
#	5 => 'autoconfirmed',
#);

# THIS MUST BE ADDED.  This prevents direct access to the Auth file.
define('SMF_IN_WIKI', true);

# Load up the extension
require_once "$IP/extensions/Auth_SMF.php";
$wgAuth = new Auth_SMF();
```

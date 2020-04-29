# Organizing AEM Dispatcher Configuration
In this project we will learn how to organize apache configuration files for an AEM Server.
## Prerequisites
* Apache > 2
* Dispatcher > 4.0

## Goal
1. Keep httpd.conf as vanilla/OOB as we can, 
2. Dispatcher configuration to be consistent across environments.

## Environment
For our learning purpose, www.acme.com has two sets of servers, authoring and publishing.
Rules like filter, cache differ based on if the server is an authoring server, or publisher.
With our goal to have consistent configuration, we will move the dependency into environment variables.

# Apache Environment Variables
| Variable Name | Value | Notes |
| INSTANCE_TYPE | [AUTHOR/PUBLISH] | This identifies type of the instance |
| RENDER_SERVER_IP | <<IP Address of the Publish Server>> | This is the IP Address of the Publish App server |
| RENDER_SERVER_PORT | <<PORT of App Server>> | App Server Port |

# Design
* Master File to include one of Instance Type File (Author,PUBLISH) 
* Each section split as a single file, we don't want to manage entire configuration in one monolithic file.
* Instance Type will then include its own 
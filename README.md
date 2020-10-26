# platform_msgs
Generic control to platform interface messages/services/actions.

# Messages

# Services

# Actions

## PlatformGoal.action
Action message interface for control of a generic robotic platform to link with control code developed across CARES projects.
Ask a robot platform to move a given link_id to a given pose.
Note the planning and actuation of the desired request is the responsibility of the specific platform being operated. 
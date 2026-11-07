Back to [Main Project Home](https://github.com/slgrobotics/articubot_one/wiki)

-----------------------

# Dock detector interfaces

**Contents:**

- [What is this package for?](#what-is-this-package-for)
- [DockDetection message](#dockdetection-message)
- [SelectDock service](#selectdock-service)

-------------

## What is this package for?

The dock detector and the robot's navigation software need to exchange clear
messages. This package defines the forms they use, much like agreeing on what
to write on a delivery label.

One form says, “Please look for the garage dock.” Another reports where that dock
was seen and when. Each search also gets its own unique label, so an old report
from an earlier search cannot be mistaken for a new one. This package defines
the messages; the other packages do the looking and driving.

**Related packages and data:**
- https://github.com/slgrobotics/dock_detector
- https://github.com/slgrobotics/dock_detector_nav2
- https://github.com/slgrobotics/dock_detector/tree/main/media

## DockDetection message

DockDetection contains a timestamped Nav2-convention parking pose, dock_id and
caller-generated acquisition_id. Its yaw points INTO the bay. PoseStamped remains
a separate legacy/debug output from the detector.

## SelectDock service

SelectDock activates a named catalogue entry with a nonempty acquisition_id.
A successful response echoes the active ID/token. Selection clears acquisition
state and requires new scans; it does not mean that a dock has been detected.
activate=false releases only the matching active ID/token. Unknown activation or
mismatched release leaves the current selection intact. Scope this service to one
robot; it does not implement physical dock reservation or fleet access control.

-----------------------

Back to [Main Project Home](https://github.com/slgrobotics/articubot_one/wiki)

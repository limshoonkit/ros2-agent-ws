# px4_agent_control

Agentic PX4 offboard control nodes that bridge VLN / introspector agent text topics to PX4 trajectory setpoints.

```
colcon build
source install/setup.bash
```

### navigation example
```
ros2 launch px4_agent_control px4_agent_nav.launch.py
```

### search and approach example
```
ros2 launch px4_agent_control px4_agent_search_approach.launch.py
```

## ROS parameters

Both `px4_agent_nav_node` and `px4_agent_search_approach_node` accept:

| Parameter | Type | Default | Notes |
|-----------|------|---------|--------|
| `height` | double | `1.0` | Hold altitude magnitude (m); published NED z is `-abs(height)` |
| `mission_objective` | string | `""` | Goal / obstacle text for the VLN query (see launch examples) |
| `introspector_object` | string | `"Aruco Marker"` | Object name for the introspector prompt |
| `resend_command` | bool | `true` | When true, include recent VLN history in the next query. **Note:** nodes currently declare/get this under the misspelled key `resend_commnad` (typo); launch files already pass `resend_command` — align keys so overrides apply (tracked separately). |
| `resend_size` | int | `10` | Max VLN history lines included when resending. **Clamped to `[1, 100]`** after load (values outside log a warning and are adjusted). |

Launch files under `launch/` set sensible demo defaults for the fields above.

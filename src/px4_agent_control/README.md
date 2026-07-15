# px4_agent_control

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

## Parameters

| Name | Default | Notes |
|------|---------|--------|
| `height` | `1.0` | Hold altitude (m). Non-finite or `<= 0` → **1.0**; values **> 120** soft-clamped with a warning. Published NED z uses `-abs(height)`. |
| `mission_objective` | `""` | Goal / obstacle text for VLN |
| `introspector_object` | `"Aruco Marker"` | Introspector prompt object name |
| `resend_commnad` | `true` | Typo vs launch `resend_command` — param-alignment tracked separately |
| `resend_size` | `10` | VLN history lines when resending |


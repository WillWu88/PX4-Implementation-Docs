# Logging Data in PX4

This page documents how to log relevant [[UORB]] messages

## SITL Logging
- **Official Documentation Error**: put `logger_topics` in `build/px4_sitl_default/etc/logging` instead of what is documented in official documentation

### 1. Logging Format:
```txt
[topic] <frequency> <instance> 
```

#development 
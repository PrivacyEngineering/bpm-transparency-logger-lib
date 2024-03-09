# BPM transparency logging library implementation

This library showcases a transparency logger implementation for python.

Decorate an activity endpoint easily as shown in the following code example: 

```
import TiltLogger
import logging
from opentelemetry import trace
tracer = trace.get_tracer(__name__)

logger = logging.getLogger()
tl = TiltLogger("TILT",tracer)

@tl.log(concept_name = "Send Data to User", tilt = {
    "data_disclosed": ["user.id"], 
    "purposes": ["personal data access"], 
    "legal_bases": ["GDPR-6-1-b"]
    }, msg = "Send Data to User")
def respond_user_information(info,last_accessed):
    logger.debug("Respond to user")
    return info|last_accessed
```

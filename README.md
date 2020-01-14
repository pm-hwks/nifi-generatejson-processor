# nifi-generatejson-processor
A NiFi processor to generate JSON based on json-data-generator java library (https://github.com/acesinc/json-data-generator). 
<div style="text-align:center"><img src ="./screenshots/logo.png" width="95%"/></div>

[![Build Status](https://travis-ci.org/pm-hwks/nifi-generatejson-processor.svg?branch=master)](https://travis-ci.org/pm-hwks/nifi-generatejson-processor)

## Installation :

1. Download the nar file from github release tab and drop it in the NiFi lib folder $NIFIROOT/lib/
2. Restart NiFi to load the new processor

<div style="text-align:center"><img src ="./screenshots/install.png" width="95%"/></div>


## Usage

1. Drag and drop the "GenerateJSON" processor into the NiFi Canvas

2. Configure the processor and add following text to the "Custom Text" attribute. You can leave other attributes as is

    Note: This is a sample template. plz refer to "Workflow Steps" section here in https://github.com/acesinc/json-data-generator for more details
    
    
    {
        "timestamp": "nowTimestamp()",
        "system": "random('BADGE', 'AUDIT', 'WEB')",
        "actor": "bob",
        "action": "random('ENTER','LOGIN','EXIT', 'LOGOUT')",
        "objects": ["Building 1"],
        "location": {
            "lat": "double(-90.0, 90.0)",
            "lon": "double(-180.0, 180.0)"
        },
        "message": "Entered Building 1"
    }

<div style="text-align:center"><img src ="./screenshots/custom_text.png" width="95%"/></div>

3. Run the Flow

<div style="text-align:center"><img src ="./screenshots/flow_after_start.png" width="95%"/></div>

4. Review the flow files

    Notice the random values generated for the system based on the inputs and differences

Flow File 1
<div style="text-align:center"><img src ="./screenshots/first_flowfile.png" width="95%"/></div>

Flow File 2
<div style="text-align:center"><img src ="./screenshots/second_flowfile.png" width="95%"/></div>


## Build Notes

1. Built & tested using JDK 1.8
2. When using Intellij make sure the project SDK is pointing to JDK 1.8 otherwise the surefire tests may fail

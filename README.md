# moment_tz

Bundle for Salesforce with moment timezone

**Component:**

```
<aura:component implements="force:appHostable,flexipage:availableForAllPageTypes,flexipage:availableForRecordHome,force:hasRecordId,forceCommunity:availableForAllPageTypes,force:lightningQuickAction" access="global" >
    <!-- Include the static resource -->
    <ltng:require scripts="{!$Resource.moment_tz}" afterScriptsLoaded="{!c.init}" />
    <!-- Display the current time -->
    <aura:attribute name="currentTime" type="String"/>
    <div>
        Current Time: {!v.currentTime}
    </div>
</aura:component>
```

**Controller:**

```
({
    init : function(component, event, helper) {
        // Load Moment Timezone from the static resource
        var moment = window.moment;
        moment.tz.setDefault("America/New_York");   
        // Get the current time
        var now = moment();
        component.set("v.currentTime", now.format());
    }
})
```

**Important:** to ensure that the code runs in the global scope of the LWS sandbox instead of attempting to access the actual global scope, modify the script code to assign self to global.

```
(function (global) {
  global = global || self;
  global.myFunction = function () {};
})(this);
```

https://developer.salesforce.com/docs/platform/lwc/guide/security-lwsec-js.html

**Result**

```
Current Time: 2024-06-01T18:40:09-04:00
```


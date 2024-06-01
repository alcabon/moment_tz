# moment_tz

Bundle for Salesforce with moment timezone

**Component:**

<aura:component implements="force:appHostable,flexipage:availableForAllPageTypes,flexipage:availableForRecordHome,force:hasRecordId,forceCommunity:availableForAllPageTypes,force:lightningQuickAction" access="global" >
    <!-- Include the static resource -->
    <ltng:require scripts="{!$Resource.moment_tz}" afterScriptsLoaded="{!c.init}" />
    <!-- Display the current time -->
    <aura:attribute name="currentTime" type="String"/>
    <div>
        Current Time: {!v.currentTime}
    </div>
</aura:component>

**Controller:**

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



---
weight: 90
title: Smart rules collection
layout: redirect
---

<a name="business"></a>

{{< product-c8y-iot >}} includes preset global smart rule types. Each global smart rule type provides different parameters to configure.

The following types are available:


<table>
<thead>
<colgroup>
       <col style="width: 30%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Smart rule</th>
<th align="left">Functionality</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><a href="#alarm-sms">On alarm send SMS</a></td>
<td align="left">If an alarm is created, an SMS is sent.</td>
</tr>
<tr>
<td align="left"><a href="#alarm-email">On alarm send email</a></td>
<td align="left">If an alarm is created, an email is sent.</td>
</tr>
<tr>
<td align="left"><a href="#alarm-escalate">On alarm escalate it</a></td>
<td align="left">If an alarm is created, an email or SMS is sent.</td>
</tr>
<tr>
<td align="left"><a href="#alarm-severity">On alarm duration increase severity</a></td>
<td align="left">If an alarm is active for a certain time, the severity is increased.</td>
</tr>
<tr>
<td align="left"><a href="#geofence-alarm">On geofence create alarm</a></td>
<td align="left">If a geofence border is crossed, an alarm is created.</td>
</tr>
<tr>
<td align="left"><a href="#geofence-email">On geofence send email</a></td>
<td align="left">If a geofence border is crossed, an email is sent.</td>
</tr>
<tr>
<td align="left"><a href="#calculate-energy">Calculate energy consumption</a></td>
<td align="left">Creates consumption data points based on data from an electric, gas, or water meter.</td>
</tr>
<tr>
<td align="left"><a href="#missing-measurements">On missing measurements create alarm</a></td>
<td align="left">If no new measurement data has been received for a specified time, an alarm is created.</td>
</tr>
<tr>
<td align="left"><a href="#alarm-operation">On alarm execute operation</a></td>
<td align="left">If a certain alarm occurs, the specified operation will be sent to the device.</td>
</tr>
<tr>
<td align="left"><a href="#threshold-explicit">On measurement explicit threshold create alarm</a></td>
<td align="left">If the measurement value enters or leaves the red range, a CRITICAL alarm is generated or cleared. This rule is similar to the rule "On measurement threshold create alarm". However, it provides the red threshold value explicitly.</td>
</tr>
<tr>
<td align="left"><a href="#threshold-alarm">On measurement threshold create alarm</a></td>
<td align="left">If the measurement value enters or leaves the red/yellow range, an alarm is created or respectively cleared. This rule extracts the thresholds values from the device or data point library.</td>
</tr>
</tbody>
</table>

>**Info:** In certain rule parameters, various trigger fields can be used as variables, see [Smart rule variables](#smart-rule-variables) at the end of this section.  


<a name="alarm-sms"></a>
### On alarm send SMS

**Functionality**

If an alarm is created, an SMS is sent.

> **Info:** This rule is only available if your tenant has a configured SMS provider.

**Parameters**

The rule uses the following parameters:

![On alarm send SMS](/images/users-guide/cockpit/cockpit-globalsmartrules-sendsms.png)

<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">On alarm matching</td>
<td align="left">The types of alarms triggering the rule. For each newly created alarm with one of these types in the list the rule is triggered.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Send SMS</td>
<td align="left"><strong>Phone number</strong>: Target phone number. It is recommended to include mobile country code for all numbers, for example, "+49" or "0049" for Germany. Multiple numbers can be separated by a comma (",", do not use a space!).<br> <strong>Message</strong>: Text of SMS with max. 160 characters. You can use variables of the form #{name}, see <a href="#smart-rule-variables" class="no-ajaxy">Smart rule variables</a>.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

You can select a single group or a single device (just one, not multiple). To enable it in other assets or devices you must navigate to each context and enable it there. Afterwards you're able to see all target assets or devices in a list with the title "Active for target asset or devices" in the smart rule detail

**Troubleshooting**

* Verify that the alarm was created and not duplicated from somewhere.

* Check if the device is in [maintenance](/users-guide/device-management#maintenance-mode) mode. In this case no new alarm will be created because of suppression policy.

* If you have configured an alarm mapping rule (see [Administration > Alarm mapping](/users-guide/administration#reprio-alarms)) which changes the alarm severity, the alarm may have different severity than expected.

>**Important:** There is a limit of 160 characters as a total count. If you use variables and after applying the variables the text counts more than 160 characters the SMS will not be sent.

<a name="alarm-email"></a>
### On alarm send email

**Functionality**

If an alarm is created, an email is sent.

>**Info:** Note that the corresponding emails are send with "text/html" as content type.

**Parameters**

The rule uses the following parameters:

![On alarm send email](/images/users-guide/cockpit/cockpit-globalsmartrules-sendemail.png)

<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">On alarm matching</td>
<td align="left">The types of alarms triggering the rule. For each newly created alarm with one of these types in the list the rule is triggered.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Send email</td>
<td align="left"><strong>Send to:/Send CC to:/Send BCC to</strong>: Email addresses for sending the email to. Multiple addresses can be separated by a comma (",", do not use a space!).<br><strong>Reply to</strong>: Address to be used to reply to the message.<br> <strong>Subject</strong>: Subject of email. You can use a variable of the form #{name}, see <a href="#smart-rule-variables" class="no-ajaxy">Smart rule variables</a>.<br> <strong>Message</strong>: Text of the email. You can use a variable of the form #{name}, see <a href="#smart-rule-variables" class="no-ajaxy"> Smart rule variables</a>.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

* Verify that the alarm was created and not duplicated from somewhere.

* Check if the device is in [maintenance](/users-guide/device-management#maintenance-mode) mode. In this case no new alarm will be created because of suppression policy.

* If you have configured an alarm mapping rule (see [Administration > Alarm mapping](/users-guide/administration#reprio-alarms)) which changes the alarm severity, the alarm may have different severity than expected.

* Check your spam folder.

<a name="alarm-escalate"></a>
### On alarm escalate it

**Functionality**

If an alarm is created, sends email or SMS.

**Parameters**

The rule uses the following parameters:

![On alarm escalate](/images/users-guide/cockpit/cockpit-globalsmartrules-escalate.png)

<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">On alarm matching</td>
<td align="left">The types of alarms triggering the rule. For each newly created alarm with one of these types in the list the rule is triggered.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Escalate as follows</td>
<td align="left">Escalation steps processed in a chain. <br> Click <strong>Add step</strong> to define at least one step: <br> <strong>Type</strong>: Type of action executed in the step. Possible values are: <br> - Email (see "On alarm send email" rule for parameter descriptions). <br> - SMS (see "On alarm send SMS" rule for parameter descriptions). <br> <strong>Condition</strong>: The condition applied when the rule will be executed. Possible values are: <br> - Always: Action will always be executed. <br> - Always: If step N failed. Only phone steps may fail. The step is marked as failed once all retries have been made without a successful call. This option only appears if there already is a phone step configured that can be referred to.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>


**Troubleshooting**

* Verify that the alarm was created and not duplicated from somewhere.

* Check if the device is in [maintenance](/users-guide/device-management#maintenance-mode) mode. In this case no new alarm will be created because of suppression policy.

* If you have configured an alarm mapping rule (see [Administration > Alarm mapping](/users-guide/administration#reprio-alarms)) which changes the alarm severity, the alarm may have different severity than expected.


<a name="alarm-severity"></a>
### On alarm duration increase severity

**Functionality**

If an alarm is active for a certain time, the severity is increased.

**Parameters**

The rule uses the following parameters:

![On alarm increase severity](/images/users-guide/cockpit/cockpit-globalsmartrules-severity.png)

<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">On alarm matching</td>
<td align="left">The types of alarms triggering the rule. For each newly created alarm with one of these types in the list the rule is triggered.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Increase alarm severity</td>
<td align="left">Duration, an alarm must be active, before increasing the severity.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

**Description**

When a configured type of alarm is raised, it starts monitoring how long the alarm stays active.

If the alarm is still active after the specified duration, the severity will be increased one level, for example, from MINOR to MAJOR.

If the alarm has reached CRITICAL, it will stop monitoring because there is no further action possible.

> **Info:** The rule checks once a minute if the configured duration has been exceeded. Therefore it might happen that the alarm severity won't change in the second it exceeds the duration but only after the following check.

<a name="geofence-alarm"></a>
### On geofence create alarm

**Functionality**

If a geofence border is crossed, an alarm is created.

The rule can be configured for entering or leaving the geofence, or both. Existing alarms are cleared when the opposite condition is true again, for example, if a tracked car which has left the geofence area is re-entering the geofence area.

**Parameters**

The rule uses the following parameters:

![On geofence create alarm](/images/users-guide/cockpit/cockpit-globalsmartrules-geofencealarm.png)

|<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">On geofence violation</td>
<td align="left">Polygon that defines the borders of an area. Click <strong>Edit geofence</strong> and set the area. Double-click to add points and click and drag them to adjust.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Create alarm</td>
<td align="left"><b>Trigger:</b> Reason for triggering the alarm: "On entering", "On leaving" (the default), "On entering and leaving".<br><b>Type:</b> Type of alarm being raised. It is strongly recommended to use different types of alarms for each smart rule. If the same alarm type is used across multiple smart rules, smart rules may interfere when trying to update the same alarm type, which might lead to unexpected behavior.<br> <b>Severity:</b> Severity of alarm being raised. <br><b>Text:</b> Alarm message.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

> **Info:** In order to raise an alarm the device had to be inside the geofence at least once after creating the rule.

**Troubleshooting**

* Make sure the device was inside the geofence at least once after creating/activating the rule.

* Check if the device is in [maintenance](/users-guide/device-management#maintenance-mode) mode. No new alarm will be created because of suppression policy.

* If you have configured an alarm mapping rule (see [Administration > Alarm mapping](/users-guide/administration#reprio-alarms)) which changes the alarm severity, the alarm may have different severity than expected.

<a name="geofence-email"></a>
### On geofence send email

**Functionality**

If a geofence border is crossed by leaving the geofence area, an email is sent.

>**Info:** Note that the corresponding emails are send with "text/html" as content type.

**Parameters**

The rule uses the following parameters:

![On geofence send email](/images/users-guide/cockpit/cockpit-globalsmartrules-geofenceemail.png)

<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">On geofence violation</td>
<td align="left">Polygon that defines the borders of an area. Click <strong>Edit geofence</strong> and set the area. Double-click to add points and click and drag them to adjust.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Send email</td>
<td align="left"><strong>Send to:/Send CC to:/Send BCC to</strong>: Email addresses for sending the email to. Multiple addresses can be separated by a comma (",", do not use a space!).<br><strong>Reply to</strong>: Address to be used to reply to the message.<br> <strong>Subject</strong>: Subject of email. You can use a variable of the form #{name}, see <a href="#smart-rule-variables" class="no-ajaxy"> Smart rule variables</a>.<br> <strong>Message</strong>: Text of the email. You can use a variable of the form #{name}, see <a href="#smart-rule-variables" class="no-ajaxy"> Smart rule variables</a>.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

> **Info:** In order to perform the rule the device had to be inside the geofence at least once after creating the rule. An email is triggered on leaving the geofence area.

**Troubleshooting**

* Make sure the device was inside the geofence at least once after creating/activating the rule.

* Check your spam folder.


<a name="calculate-energy"></a>
### Calculate energy consumption

**Functionality**

Creates consumption data point based on data from an electric, gas, or water meter.

**Parameters**

The rule uses the following parameters:

![Calculate energy consumption](/images/users-guide/cockpit/cockpit-globalsmartrules-energy.png)

<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">Monitored measurement</td>
<td align="left"><strong>Fragment/Series</strong>: Name of the measurement fragment and series. The incoming measurement must have exactly the same fragment/series name as configured. When creating a rule from the data explorer, these fields are already filled in. <br> <strong>Time interval</strong>: Interval in which consumption values shall be calculated. Specifies how often per hour the consumption is calculated.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Energy consumption measurement</td>
<td align="left">Name of the measurement fragment and series that shall be generated.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

The unit of the consumption measurement is always per hour (that means, if the measurements are in "kg" the consumption will be in "kg/h").

The rule takes the last two measurements for a specified time, calculates the difference in value and time and then calculates the consumption per hour.

**Example**

The rule is configured to calculate every 20 minutes. The following measurements are coming in:
100 kg at 11:59 and 200 kg at 12:14.
At 12:20 the rule is triggered, taking the last two measurements. It calculates value and time difference. The consumption measurement created at 12:20 will therefore be 400 kg/h.
If no new measurement was created in the last period a measurement with consumption 0 will be created.

<a name="missing-measurements"></a>
### On missing measurements create alarm

**Functionality**

If no new measurement data has been received for a specified time, an alarm is created.

**Parameters**

The rule uses the following parameters:

![On missing measurements create alarm](/images/users-guide/cockpit/cockpit-globalsmartrules-missingmeasurement.png)

<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">Monitored measurement</td>
<td align="left"><strong>Type</strong>: Type of measurement. The incoming measurement must have the same type as configured. When creating a rule from the data explorer, the type is already filled in.<br> <strong>Time interval</strong>: Interval for calculating consumption values.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Create alarm</td>
<td align="left"><b>Type:</b> Type of alarm being raised. It is strongly recommended to use different types of alarms for each smart rule. If the same alarm type is used across multiple smart rules, smart rules may interfere when trying to update the same alarm type, which might lead to unexpected behavior.<br> <b>Severity: </b>Severity of alarm being raised. <br><b>Text: </b>Alarm message.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

> **Info:** The rule checks once a minute if the configured time interval was exceeded. Therefore it can take up to one minute to create the alarm after the time interval was exceeded. To check if the time interval was exceeded there must be at least one incoming measurement after the activation of the rule.

<a name="alarm-operation"></a>
### On alarm execute operation

**Functionality**

If a certain alarm occurs, the specified operation will be send to the device.


**Parameters**

The rule uses the following parameters:

![On alarm execute operation](/images/users-guide/cockpit/cockpit-globalsmartrules-operation.png)

<table>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<thead>
<tr>
<th style="text-align:left">Step</th>
<th style="text-align:left">Field</th>
<th style="text-align:left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left">1</td>
<td style="text-align:left">Rule name</td>
<td style="text-align:left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td style="text-align:left">2</td>
<td style="text-align:left">On alarm matching</td>
<td style="text-align:left">The types of alarms triggering the rule. For each newly created alarm with one of these types in the list the rule is triggered.</td>
</tr>
<tr>
<td style="text-align:left">3</td>
<td style="text-align:left">Execute operation</td>
<td style="text-align:left">The operation that will be sent. The operation is provided as JSON description. Some standard operations can be selected below the <strong>Operation</strong> field. To use a standard operation, select one, and press the arrow button at the right. This will insert the JSON of the selected operation.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

<a name="threshold-alarm"></a>
### On measurement threshold create alarm

**Functionality**

If the measurement value enters or leaves the red/yellow range, an alarm is created or respectively cleared.

The severity of alarm is determined as follows:

* If the measurement value moves into the red range, then an alarm of CRITICAL severity is created. If it moves out of the red range, the CRITICAL alarm is cleared.

* If the measurement value moves into the yellow range, then an alarm of MINOR severity is created. If it moves out of the yellow range, the MINOR alarm is cleared.

The rule uses the following parameters from the device object or data point library:

* Data point library red/yellow range: Red range when the system should create CRITICAL alarms and yellow range when the system should create MINOR alarms. Note that the data point should have at least one of red or yellow range configured.

* Object red range: Range when the system should create CRITICAL alarms. These values can be edited in the data explorer for each data point. Note that these are close intervals ([red min: red max]) that contain the lowest accepted value and the highest accepted value, see also examples below.

* Object yellow range: Range when the system should create MINOR alarms. These values can be edited in the data explorer for each data point. Note that these are half-open intervals ([yellow min : yellow max)) that contain the lowest accepted value but not the highest accepted value, see also examples below.

#### Examples

**Example 1 - Red range:**

If we set the red range to "[60;90]"

* red min: 60
* red max: 90

and the measured value is between 60 - 90 (including the values 60 and 90) as a result a CRITICAL alarm (red) will be created.

**Example 2 - Yellow range:**

If we set the yellow range to "[30;50)"

* yellow min: 30
* yellow max: 50

and the measured value is between 30 - 49 as a result a MINOR alarm (yellow) will be created. The value 50 is out of the yellow range.

**Example 3 - Red and yellow range:**

As a result of the above behavior, we can set configurations like the following:

* red min: 60
* red max: 90
* yellow min: 30
* yellow max: 60

If the measured value is 60, then as a result a CRITICAL alarm (red) will be created because red includes the value 60.

**Example 4 - Overlap:**

The red range and the yellow range can overlap. A value in this overlap range is treated as being in the yellow range.

If we set the yellow range to "[30;60)" and the red range to "[50;90]":

* red min: 50
* red max: 90
* yellow min: 30
* yellow max: 60

and the measured value is 55, a MINOR alarm (yellow) will be created.

Using these mechanisms, you can configure global threshold ranges in the data point library. These global values can then be overridden for specific objects on a case-by-case basis.

**Parameters**

The rule uses the following parameters:

![On measurement threshold create alarm](/images/users-guide/cockpit/cockpit-globalsmartrules-thresholdalarm.png)

<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">On threshold</td>
<td align="left"><strong>Fragment/Series</strong>: Name of the measurement fragment and series. The incoming measurement must have exactly the same fragment name as configured. When creating a rule from the data explorer, these fields are already filled in. <br> <strong>Data point library entry</strong>: Name of the entry in the data point library. This is used to find the default values for red and yellow ranges in case they are not configured for an individual object. Note that the unit which is set in the data point is not taken into account here.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Create alarm</td>
<td align="left"><b>Type:</b> Type of alarm being raised. It is strongly recommended to use different types of alarms for each smart rule. If the same alarm type is used across multiple smart rules, smart rules may interfere when trying to update the same alarm type, which might lead to unexpected behavior.<br> <b>Text: </b>Alarm message.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

**Description**

For each incoming measurement value, the rule performs the following steps:

* Check if the smart rule has a valid data point. If not, an alarm with MAJOR severity is sent from the rule engine (CEP) informing that the rule has an invalid configuration.

* Check if the rule is activated for the source object.

* Check if the measurement includes data for the fragment and series (configured data point's parameter).

* The data of the red and yellow range is collected from either:

- the data point library (control parameter).
- the source object (the measurement). If found, ranges from the source object's data point override are merged.

If no red/yellow ranges are defined in the merged parameters, no alarms are generated.

> **Info:** Range values defined in the source object have a higher priority than those defined in the data point library. You can also just overwrite a single value (for example yellow range max) by setting it in the source object. The other values will then be taken from the Data Point Library.

* Incoming value inside the red range: <br> If there is no active alarm of CRITICAL severity of given type for the object, create a CRITICAL alarm, else do nothing.

* Incoming value inside the yellow range: <br>If there is no active alarm of MINOR severity of given type for the object, create a MINOR alarm, else do nothing.

* Measurement outside of yellow and red range: <br>If there is an active alarm of given type for the object, clear the CRITICAL and/or MINOR alarm.

**Troubleshooting**

* Verify that the alarm was created and not duplicated from somewhere.

* Check if the device is in [maintenance](/users-guide/device-management#maintenance-mode) mode. In this case no new alarm will be created because of suppression policy.

* If you have configured an alarm mapping rule (see [Administration > Alarm mapping](/users-guide/administration#reprio-alarms)) which changes the alarm severity, the alarm may have different severity than expected.

* Check if an alarm was already cleared by the next scheduled measurements with resulting value in a green range.

> **Info:**  If you clear an alarm, you state that the alarm is resolved. A new alarm is not raised unless the device changes its state and exceeds the thresholds again.

>**Info:** Under certain circumstances, that means, if the time gap between measurements is quite large, this smart rule may raise a wrong alarm severity. If, for example, the CEP/Apama pod is restarted, the internal state is lost and therefore an alarm is raised again when it should not, resulting in a different alarm severity.


<a name="threshold-explicit"></a>
### On measurement explicit threshold create alarm

**Functionality**

If the measurement value enters or leaves the red range, a CRITICAL alarm is generated or cleared.

The severity of alarm is determined as follows:

* If the measurement value moves into red range, then the severity is CRITICAL.

* If the measurement value moves into GREEN range, no alarm is created.

> **Info:** This rule is similar to the rule "On measurement threshold create alarm". However, in this rule here the red threshold value is provided explicitly. The threshold rule "On measurement threshold create alarm" extracts the thresholds values from the device or data point library.

**Parameters**

The rule uses the following parameters:

![On measurement explicit threshold create alarm](/images/users-guide/cockpit/cockpit-globalsmartrules-measurementthreshold.png)

<table>
<thead>
<colgroup>
       <col style="width: 10%;">
       <col style="width: 20%;">
       <col style="width: 70%;">
    </colgroup><thead>
<tr>
<th align="left">Step</th>
<th align="left">Field</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">1</td>
<td align="left">Rule name</td>
<td align="left">Pre-filled with the name of the rule template. Can be modified according to your needs.</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">On threshold</td>
<td align="left"><strong>Fragment/Series</strong>: Name of the measurement fragment and series. The incoming measurement must have exactly the same fragment name as configured. When creating a rule from the data explorer, these fields are already filled in. <br> <strong>Minimum, Maximum</strong>: When a value is in the specified range [minimum; maximum], the configured alarm is raised.</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">Create alarm</td>
<td align="left"><strong>Type:</strong> Type of alarm being raised. It is strongly recommended to use different types of alarms for each smart rule. If the same alarm type is used across multiple smart rules, smart rules may interfere when trying to update the same alarm type, which might lead to unexpected behavior.<br><strong>Text:</strong> Alarm message.</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">Target asset or devices</td>
<td align="left">Select a group or device the rule shall be applied to. To activate the smart rule in other assets or devices, navigate to the respective objects and enable the smart rule. The smart rules details will show a list "Active for target asset or devices". <br>
If you leave this field empty, the smart rule will be applied to every group and device. You can then deactivate the smart rule for specific assets or devices. In this case the smart rules details will show a list "Inactive for target asset or devices". <br>
For details on activating/deactivating a smart rule, see <a href="#toggle-rules" class="no-ajaxy">To deactivate or activate a smart rule for a group or device</a>.
</td>
</tr>
</tbody>
</table>

**Troubleshooting**

* Verify that the alarm was created and not duplicated from somewhere.

* Check if the device is in [maintenance](/users-guide/device-management#maintenance-mode) mode. In this case no new alarm will be created because of suppression policy.

* If you have configured an alarm mapping rule (see [Administration > Alarm mapping](/users-guide/administration#reprio-alarms)) which changes the alarm severity, the alarm may have different severity than expected.

* Check if an alarm was already cleared by the next scheduled measurements with resulting value in a green range.

> **Info:**  If you clear an alarm, you state that the alarm is resolved. A new alarm is not raised unless the device changes its state and exceeds the thresholds again.

>**Info:** ​Under certain circumstances, that means, if the time gap between measurements is quite large, this smart rule may raise a wrong alarm severity. If, for example, the CEP/Apama pod is restarted, the internal state is lost and therefore an alarm is raised again when it should not, resulting in a different alarm severity.

<a name="smart-rule-variables"></a>
### Smart rule variables

In certain rule parameters, various trigger fields can be used as variables. When a rule is triggered, the variables are replaced by the actual values of these trigger fields.

You can use this mechanism for example to insert device names or alarm text into various outputs (email, SMS).


**Common fields to be used from all triggers (alarms, measurements, operations, events)**

<table>
<colgroup>
       <col style="width: 30%;">
       <col style="width: 70%;">
    </colgroup>
  <tr>
  <td><b>Variable</b></td>
  <td><b>Content</b></td>
  </tr>
  <tr>
    <td>#{id}</td>
    <td>Identifier of the trigger.</td>
  </tr>
  <tr>
    <td>#{type}</td>
    <td>Type of the trigger.</td>
  </tr>
  <tr>
    <td>#{source}</td>
    <td>Identifier of the source of the trigger.</td>
  </tr>
  <tr>
    <td>#{time}</td>
    <td>Timestamp of the trigger.  </td>
  </tr>
  <tr>
    <td>#{text}</td>
    <td>Text or message of the trigger.</td>
  </tr>
</table>

> **Info:** If using Apama for smart rules (shown by a subscription to Apama-ctrl in <b>Applications</b> > <b>Subscribed Applications</b> in the Administration application),
variables for times can include a time zone and time format to display the time in.
The variable #{time:TZ=America/New_York,FORMAT="HH:mm:ssZ"} for example displays the time using the time zone for New York in the format HH:mm:ssZ.
See also [Supported time zones]({{< link-apama-webhelp >}}/index.html#page/apama-webhelp%2Fco-DevApaAppInEpl_supported_time_zones.html)
and [Format specification for the TimeFormat functions]({{< link-apama-webhelp >}}/index.html#page/apama-webhelp%2Fco-DevApaAppInEpl_format_specification_for_the_time_format_plug_in_functions.html)
in the Apama documentation.

**Fields specific for alarms**

<table>
<colgroup>
       <col style="width: 30%;">
       <col style="width: 70%;">
    </colgroup>
  <tr>
  <td><b>Variable</b></td>
  <td><b>Content</b></td>
  </tr>  
  <tr>
    <td>#{status}</td>
    <td>Status of the alarm: ACTIVE, ACKNOWLEDGED or CLEARED.</td>
  </tr>
  <tr>
    <td>#{severity}</td>
    <td>Severity of the alarm: CRITICAL, MAJOR, MINOR or WARNING.</td>
  </tr>
  <tr>
    <td>#{count}</td>
    <td>Number of times the alarm has been sent. Repeating alarms for the same device and same alarm type are de-duplicated into one alarm.</td>
  </tr>
</table>

**Fields specific for operations**

<table>
<colgroup>
       <col style="width: 30%;">
       <col style="width: 70%;">
    </colgroup>
  <tr>
  <td><b>Variable</b></td>
  <td><b>Content</b></td>
  </tr>  
  <tr>
    <td>#{status}</td>
    <td>Status of the operation: SUCCESSFUL, FAILED, EXECUTING or PENDING.</td>
  </tr>
</table>


**Fields specific for measurements**

<table>
<colgroup>
       <col style="width: 30%;">
       <col style="width: 70%;">
    </colgroup>
  <tr>
  <td><b>Variable</b></td>
  <td><b>Content</b></td>
  </tr>  
  <tr>
    <td>#{valueFragment}</td>
    <td>Measurement value fragment name.</td>
  </tr>  
  <tr>
    <td>#{valueSeries}</td>
    <td>Measurement series fragment name.</td>
  </tr>
  <tr>
    <td>#{value}</td>
    <td>Value from the sensor.</td>
  </tr>
  <tr>
    <td>#{unit}</td>
    <td>Unit being used, for example "mm", "lux".</td>
  </tr>
</table>


Moreover, the following pattern is supported:

<table>
<colgroup>
       <col style="width: 30%;">
       <col style="width: 70%;">
    </colgroup>
  <tr>
  <td><b>Variable</b></td>
  <td><b>Content</b></td>
  </tr>  
  <tr>
    <td>#{X.Y} or #{X.Y.Z} </td>
    <td>The property field information available in extra params or nested structure params of the trigger.</td>
  </tr>  
</table>

#### Example

**{{< product-c8y-iot >}} trigger**

```json
{
  "source":{
    "id":"10200"
  },
  "type":"TestEvent",
  "text":"sensor was triggered",
  "time":"2014-03-03T12:03:27.845Z",
  "c8y_Position":{
    "lat":2,
    "lng":2
  },
  "c8y_evtdata":{
    "data1":111,
    "date2":222,
    "evtInnerData":{
      "indate1":333,
      "indate2":444
    }
  }
}
```

Here we can for example define the following variables:

<table>
<colgroup>
       <col style="width: 30%;">
       <col style="width: 70%;">
    </colgroup>
  <tr>
  <td><b>Variable</b></td>
  <td><b>Content</b></td>
  </tr>  
  <tr>
    <td>#{ c8y_Position.lat} </td>
    <td>Gets latitude value.</td>
  </tr>  
  <tr>
    <td>#{ c8y_evtdata.data1} </td>
    <td>Gets data1 value.</td>
  </tr>  
  <tr>
    <td>{ c8y_evtdata. evtInnerData . indate1} </td>
    <td>Gets nested structure value.</td>
  </tr>  
  <tr>
    <td>#{source.X.Y} </td>
    <td>The property field information from the source device (ManagedObject) of the trigger. For example:
    <br> #{source.c8y_Hardware.serialNumber} > Serial number of the device.
    <br> #{source.c8y_Notes} > Note field of the device.</td>
  </tr>  
</table>

> **Important:** In case the variable does not exist or is misspelled, no substitution will occur.
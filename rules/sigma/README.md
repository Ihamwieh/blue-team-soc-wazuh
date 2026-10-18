<group name="windows,sysmon,sigma,">

  <rule id="100120" level="8">
    <if_sid>61603</if_sid>

    <field name="win.eventdata.image" type="pcre2">(?i)\\whoami\.exe$</field>
    <field name="win.eventdata.commandLine" type="pcre2">(?i)(/priv|-priv)</field>

    <description>Sigma: Security Privileges Enumeration via whoami.exe</description>

    <mitre>
      <id>T1033</id>
    </mitre>

    <group>sysmon_event1,discovery,</group>
  </rule>

</group>

# about_Broker_EntitlementPolicy
## TOPIC
    Citrix Broker SDK - Desktop and Application Entitlement Policy 

## SHORT DESCRIPTION
    Controls end-user entitlement to desktop and application sessions provided 
    from a pool of shared machines. 

## LONG DESCRIPTION
    The site's entitlement policy defines rules controlling users' entitlements 
    to desktop and application sessions from pools of shared machines. Each pool 
    is defined by a desktop group. 

    The entitlement policy comprises a set of rules. Each rule grants users a 
    single entitlement to a desktop or application session in a specified 
    desktop group. The policy can  be applied only to groups of desktop kind 
    Random. For desktop entitlements multiple rules can apply to the same group, 
    however for application entitlements only a single rule can apply to a given 
    group. 

    When the user starts a session by selecting an entitlement the behavior 
    depends on the session-support property of the desktop group: 

    o   For single-session groups the user is temporarily assigned a machine 
        selected at random from the group to provide their session. When the 
        session ends, the machine is returned to the pool of available machines. 
    o   For multi-session groups the user session is provided by the machine 
        that is least loaded within the group when the session is launched. 

    If multiple desktop entitlement rules for the same group contain the same 
    user, the user can have as many desktop sessions from the group concurrently 
    as they have entitlements. 

    Although only a single application entitlement rule can be defined for a 
    group, a user can still launch multiple applications from that group because 
    the applications all run within that entitlement's single session. 

    Rules for desktop and application session entitlements are distinct. Desktop 
    entitlements are managed through the BrokerEntitlementPolicyRule SDK object, 
    and application rules through the BrokerAppEntitlementPolicyRule object. 

    Desktop entitlement rules can be created only for desktop groups with 
    delivery types DesktopsOnly or DesktopsAndApps, whereas an application 
    entitlement rule can be created only for delivery types AppsOnly or 
    DesktopsAndApps. 

    For desktop groups with delivery type DesktopsAndApps, typically one or more 
    desktop session entitlement rules together with a single application session 
    entitlement rule exist. 

    For an entitlement granted by the entitlement policy to be available to a 
    user, the site's access policy must also grant them access to the desktop 
    group. 

## ENTITLEMENT POLICY RULES
    Each entitlement policy rule has the following key properties: 

    o   The desktop group to which it applies (one rule only ever applies 
        to one group) 
    o   The users to whom the entitlement is granted 

    Additionally for desktop entitlement rules, the following properties exist: 

    o   The published name of the entitlement (visible to the user) 
    o   Any properties that a desktop session launched using the entitlement 
        should use that differ from the defaults specified on the desktop group 

    If multiple desktop entitlements are available to a user from the same group 
    the resultant desktop session properties may differ depending on which 
    entitlement the user selects to start the session. 

    Each rule can be individually enabled or disabled. A disabled rule is 
    ignored when the entitlement policy is evaluated. 

  USER FILTERS (FULL) 
    Each rule has two user filters, an include filter and an exclude filter: 

    o   The include filter contains users and user groups that are granted 
        an entitlement to a session 
    o   The exclude filter contains users and user groups that are denied 
        an entitlement to a session 

    If the include filter of a rule contains multiple instances of a user 
    (either explicit or implicit), they get only one entitlement by that rule. 

    Entries in the exclude filter take priority, so if a user appears explicitly 
    or implicitly in both filters, access is denied. Typically, you use this 
    filter to exclude a user or group of users who would otherwise gain access 
    because they are members of a user group specified in the include filter. 

    Because all rules are independently evaluated, the exclude filter can only 
    exclude users who would otherwise gain an entitlement through the same 
    rule's include filter. That is, if a user is in a rule's include filter but 
    not its exclude filter, the rule is guaranteed to grant that user a session 
    entitlement irrespective of whether the user appears in the exclude filter 
    of other rules. 

    If a filter contains a user group that contains other users and groups, the 
    filter implicitly includes all of those users and groups. 

    By default the exclude filter is disabled. 

    To maintain entitlement policy rules that can be fully displayed and edited 
    with Citrix Studio, use the simplified user filter model below and do not 
    use the exclude filter. 

  USER FILTERS (SIMPLIFIED) 
    The included user filter described above also supports a simplified usage 
    model where the filter itself is disabled. When this is done, any user who 
    has access to the desktop group through the access policy is implicitly 
    granted an entitlement to a session through the entitlement policy rule 
    without the need to list the user in the rule's include filter. 

    This is useful in cases where the access policy for the desktop group 
    already explicitly specifies the users who should have access. 

    Even if the include filter is disabled, the exclude filter can still be used 
    to deny the entitlement from users who would otherwise gain access through 
    the access policy alone. 

  ADDITIONAL DESKTOP ENTITLEMENT RULE PROPERTIES 
    Desktop entitlement rules specify the following additional properties: 

    o   PublishedName 
    o   Description 
    o   IconUid 
    o   ColorDepth 
    o   SecureIcaRequired 

    The published name, description, and icon UID properties apply to the 
    desktop entitlement itself and determine the way in which the entitlement is 
    presented to the user in, for example, StoreFront. 

    The color depth and secure ICA properties apply to the desktop session that 
    is obtained when the entitlement is used. 

    In all cases, these properties can be explicitly specified. However, a null 
    value (the default) means that the corresponding property is taken from the 
    desktop group to which the rule applies. This inheritance from groups is 
    dynamic; if the property of the group changes, the property of the 
    entitlement changes too. 

## NOTES
    If a rule grants an entitlement to a user group, the session entitlement 
    applies to the individual user who selects the entitlement. However, this 
    does not prevent a different user in the same user group from using the 
    same entitlement concurrently. So, a rule that grants an entitlement to a 
    user group containing multiple users allows each user concurrent access to a 
    single session from the desktop group. 

    The total number of entitlements defined by the policy may exceed the number 
    of machines available, or the maximum allowed sessions, from the desktop 
    group. A user attempting to use an entitlement when no further resources are 
    available receives a no-desktop-available error. 

    If a session launched through an entitlement is active when the entitlement 
    rule is deleted, the session continues unaffected. However: 

        o   When the user ends the session, they cannot start a new one if the 
            deleted rule was their only entitlement to a session in that group 
        o   If the user disconnects the session, they cannot reconnect to it 

## SEE ALSO
    about_Broker_Policies 
    about_Broker_AccessPolicy 
    about_Broker_AssignmentPolicy 
    about_Broker_Applications 
    New-BrokerEntitlementPolicyRule 
    Get-BrokerEntitlementPolicyRule 
    Set-BrokerEntitlementPolicyRule 
    Rename-BrokerEntitlementPolicyRule 
    Remove-BrokerEntitlementPolicyRule 
    New-BrokerAppEntitlementPolicyRule 
    Get-BrokerAppEntitlementPolicyRule 
    Set-BrokerAppEntitlementPolicyRule 
    Rename-BrokerAppEntitlementPolicyRule 
    Remove-BrokerAppEntitlementPolicyRule 

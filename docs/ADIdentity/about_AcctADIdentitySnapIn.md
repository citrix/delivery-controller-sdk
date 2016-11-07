# about_AcctADIdentitySnapIn

## TOPIC
    about_AcctADIdentitySnapin

## SHORT DESCRIPTION
    The Active Directory Identity Service PowerShell snap-in provides
    administrative functions for the Active Directory Identity Service.

## COMMAND PREFIX
    All commands in this snap-in have the noun prefixed with 'Acct'.

## LONG DESCRIPTION
    The Active Directory Identity Service PowerShell snap-in enables both local
    and remote administration of the Active Directory Identity Service.  It
    provides facilities to store details about Active Directory computer
    accounts that the Machine Creation Service can use.

    The snap-in provides two main entities:

    Identity
        A representation of an Active Directory computer account that reflects
        the state of the account within the context of the Machine Creation
        Service.  When an account is created by or imported into the Active
        Directory Identity Service, the account password is stored.  Once the
        account is consumed by the Machine Creation Service, the  
        password is discarded.  For accounts registered with the Active
        Directory Identity Service, identities hold the following additional
        state information.

        Available
            The Active Directory account is registered with the service, the
            password for the account is known, and the account is available to
            be consumed by another service.  Accounts that are successfully
            created with the New-AcctADAccount command or imported using the
            Add-ADAccount command, are initially assigned this state.

        InUse
            The Active Directory account is registered and has been consumed by
            another service.  The password for the account is no longer known
            to the service.

        Error
            The Active Directory account is registered, but is missing,
            disabled, or locked within Active Directory.  Accounts that are not
            successfully created with the New-AcctADAccount command or imported
            using the Add-ADAccount command appear in this state.  Use the
            Update-AcctADAccount and Repair-AcctADAccount commands  
            to resolve issues with accounts in this state.

        Tainted
            The Active Directory account is registered and has been released
            by all the consuming services, but cannot be made available for use
            as the password is no longer known.  Use the Repair-AcctADAccount
            command to reset account passwords and restore the
            account state to 'Available'.

        Identities can also be marked as 'Locked' by the Machine Creation
        Service to indicate that they are in use and must not be changed.
        These services are also responsible for unlocking the Active Directory
        accounts when they no longer require exclusive access.  Use the  
        Unlock-AcctADAccount command to allow the lock to be
        overriden, if necessary.

    Identity Pool
        Containers for identities that can be configured with all the
        information required for new Active Directory accounts to be created.
        Alternatively, identity pools can be populated by importing accounts
        that already exist in Active Directory.  All accounts registered with
        the Active Directory Identity Service must be placed into one of these
        containers.  An identity can belong to more than one identity pool, but
        the state of the identity cannot be different in each pool.  For
        example, an identity that is in use will be marked 'InUse' in all the
        identity pools of which it is part.

        To avoid conflicting changes, identity pools can also be marked as 'Locked'  
		during operations that modify the content of a pool.  These         
        operations are also responsible for unlocking the identity pool.  Use the
        unlock-AcctIdentityPool command to allow the lock to be overridden,
        if necessary.

## ACTIVE DIRECTORY PERMISSIONS
    Account Creation (using the New-AcctADAccount command)
        To use PowerShell to create new Active Directory accounts, the runspace
        must be run using an account with sufficient permissions in the
        required Active Directory container (specified by the identity pool
        organizational unit parameter) for accounts to be created.

    Import Accounts (using the Add-AcctADAccount command)
        There are two modes for this operation: situations where the Active
        Directory account passwords are known and situations where the
        passwords are not known.

        If the account passwords are known, the accounts can be imported
        without the need for administrative permissions in Active Directory.
        The accounts are imported and the password provided is used to change
        the existing password.

        If the passwords are not known, the runspace must be run using an account
        that has permissions to reset the password for the accounts.

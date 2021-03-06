Hidden Settings for console
***************************

On this page you can find some settings that you won't find within the Zammad UI.
Those settings might come in handy as it can change Zamnmads behavior. 

.. Note:: Please note that this is not a full command list, if you're missing commands, feel free to ask over at our `Community <https://community.zammad.org>`_.

Send all outgoing E-Mails to a BCC-Mailbox
------------------------------------------

This option allows you to send all outgoing E-Mails (not notifications) to a specific mailbox.
Please note that this shouldn't be a mailbox you're importing already! This will apply to all groups and is a global setting.
::
 
 Setting.set('system_bcc', 'alias@domain.tld')

You can easily check the current BCC-Setting by running the following: 
::
 
 Setting.get('system_bcc')


Activate counter on grouped overviews
-------------------------------------

This is a hidden setting which you can only set via Command-Line.
This will globally enable a ticket number value in each heading for grouped elements.
::
  
  Setting.set('ui_table_group_by_show_count', true)	# enable counter on grouped overviews
  Setting.set('ui_table_group_by_show_count', false)	# disable counter on grouped overviews
  Setting.get('ui_table_group_by_show_count')		# get current setting (if NIL, it's false)

.. image:: /images/console/ui_table_group_by_show_count-example.png


Default Ticket type on creation
-------------------------------

Zammad allows you to define the default article type upon Ticket creation. By default this will be a incoming phone call.
You can choose between ``phone-in`` (incoming call, **default**), ``phone-out`` (outgoing call) and ``email-out``  (Sending an E-Mail out).
::
  
  Setting.set('ui_ticket_create_default_type', 'email-out')
  
To check what setting is set currently, simply run
::
  
  Setting.get('ui_ticket_create_default_type')


Adding a warning to the ticket creation process
-----------------------------------------------

If in case you need to give your agent a note or warning during ticket creation, you can do so with the below command.
You can use three different warnings for Incoming Calls ``:"phone-in"=>""``, Outgoing Calls ``:"phone-out"=>""`` and Outgoing E-Mails ``:"email-out"=>""``.
::
  
  Setting.set('ui_ticket_create_notes', {:"phone-in"=>"You're about to note a incoming phone call.", :"phone-out"=>"You're about to note an outgoing phone call.", :"email-out"=>"You're going to send out an E-Mail."})

.. Note:: You can use those three sub-settings independently, if you e.g. don't need a warning on incoming calls, simply leave out ``:"phone-in"=>""`` out of the setting.
  The setting itself is done within an array ( ``{}`` ).
  

To check what's currently set, you can use:
::
  
  Setting.get('ui_ticket_create_notes')

Sample of the above setting:
.. image:: /images/console/ui_ticket_create_notes.gif


Show E-Mail-Address of customer on customer selection (Ticket-Creation)
-----------------------------------------------------------------------

By default Zammad will not display the E-Mail-Addresses of customers.
The below option allows you to change this behavior.
::
  
  Setting.set('ui_user_organization_selector_with_email', true)

Get the current state of this setting with:
::
  
  Setting.get('ui_user_organization_selector_with_email')


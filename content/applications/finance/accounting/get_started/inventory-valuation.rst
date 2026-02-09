===================
Inventory valuation
===================

A company’s inventory valuation should include all available stock. Accurately recording this value
in the accounting records ensures a true representation of the company's current asset value.

The Accounting app processes journal entries when vendor bills or invoices are registered, either
periodically or on demand. In contrast, the :doc:`Inventory <../../../inventory_and_mrp/inventory>`
app maintains real-time stock valuation based on physical item movement.

.. seealso::
   :doc:`../../../inventory_and_mrp/inventory/inventory_valuation/cheat_sheet`

.. _accounting/inventory-valuation/accounting-standards:

Accounting standards
====================

In accounting, the Continental and Anglo-Saxon methods differ in when they recognize inventory
expenses and how this impacts :ref:`journal entries <accounting-entries>`:

- The Continental accounting records the cost of goods upon receipt into stock, regardless of when
  they are sold.
- The Anglo-Saxon accounting recognizes the cost of goods sold (COGS) when products are sold
  or delivered to customers.

.. note::
   The periodic accounting method is often associated with Continental standards, while the
   perpetual method is commonly used with Anglo-Saxon standards. However, companies may choose a
   different accounting :ref:`valuation method <accounting/inventory-valuation/valuation-method>`
   based on their specific needs.

.. _accounting/inventory-valuation/configuration:

Configuration
=============

Go to :menuselection:`Accounting --> Configuration --> Settings`, then scroll to the
:guilabel:`Inventory Valuation` section to set the following company-level options:

- :ref:`Inventory Valuation <accounting/inventory-valuation/valuation-method>`: Set the valuation
  method as perpetual or periodic.
- :guilabel:`Periodic Valuation`: Set the :ref:`closing entry
  <accounting/inventory-valuation/closing-entry>` process as :guilabel:`Manual`, :guilabel:`Daily`,
  or :guilabel:`Monthly`.
- :ref:`Inventory Cost Method <costing-methods>`
- :guilabel:`Valuation Account`: Asset account used to record the financial value of physical stock.
- :guilabel:`Journal`: Journal where inventory valuation entries are posted.
- :guilabel:`Other accounts can be defined on "Inventory Loss" and "Production" on dedicated
  locations`: If needed, click :guilabel:`locations`, and in the :guilabel:`Locations` list view:

  - Inventory Loss: Click :guilabel:`Asset` or :guilabel:`Inventory adjustment` and, in the
    :guilabel:`Accounting information` section, set the :guilabel:`Loss Account`.
  - Production: Click :guilabel:`Production` and, in the :guilabel:`Accounting information` section,
    set the :guilabel:`Cost of Production` expense account.

.. note::
   Default accounts, valuation, and cost methods can be overridden for each product category.

.. tip::
   In :guilabel:`Perpetual` valuation, it is recommended to set the :guilabel:`Periodic Valuation`
   to :guilabel:`Manual` and generate closing entries only when a fiscal period closes, or when
   accounting reports require synchronization with inventory stock.

.. _accounting/inventory-valuation/valuation-method:

Valuation methods
-----------------

Two accounting practices are used for maintaining inventory records, each differing in how and when
inventory costs are recognized:

- :guilabel:`Periodic (at closing)` or Continental valuation records entries only during the
  valuation closing process. Inventory movements are tracked physically but not automatically
  synchronized with financial records.
- :guilabel:`Perpetual (at invoicing)` or Anglo-Saxon valuation records entries in real-time as
  inventory moves occur. Inventory movements are immediately synchronized with financial records
  when bills are received or invoices are issued.

.. _accounting/inventory-valuation/valuation-account:

Valuation account
-----------------

The :guilabel:`Valuation account` records the inventory value listed as a current asset on the
balance sheet. How :guilabel:`the Valuation account` tracks inventory asset value depends on the
selected :ref:`valuation method <accounting/inventory-valuation/valuation-method>`:

- Periodic: The valuation account remains unchanged between closing periods and is only updated when
  a :ref:`closing entry <accounting/inventory-valuation/closing-entry>` is generated or an
  :doc:`inventory adjustment
  <../../../inventory_and_mrp/inventory/warehouses_storage/inventory_management/count_products>` is
  recorded.
- Perpetual: The valuation account updates in real-time for each posted invoice or vendor bill, and
  when a :ref:`closing entry <accounting/inventory-valuation/closing-entry>` is generated or an
  :doc:`inventory adjustment
  <../../../inventory_and_mrp/inventory/warehouses_storage/inventory_management/count_products>`
  is recorded.

  .. note::
     Stock movements from product receipts and deliveries are displayed in the :guilabel:`Stock
     Variation` section of the :ref:`Inventory valuation report
     <accounting/inventory-valuation/inventory-valuation-report>` before they are billed or
     invoiced.

.. _accounting/inventory-valuation/variation-account:

Variation account
~~~~~~~~~~~~~~~~~

The :guilabel:`Variation account` is used to record inventory variations for the period covered by
the :ref:`closing process <accounting/inventory-valuation/closing-entry>` and can be updated during
:ref:`configuration <accounting/inventory-valuation/configuration>`. To do so, follow these steps:

#. Activate the :ref:`developer mode <developer-mode>`.
#. Find the :guilabel:`Valuation Account` field and click the :icon:`oi-arrow-right`
   :guilabel:`(right arrow)` to open the :guilabel:`Stock Valuation` account.
#. Update the :guilabel:`Variation Account`.

.. _accounting/inventory-valuation/inventory-valuation-report:

Inventory valuation report
==========================

The :guilabel:`Inventory Valuation` report provides an accurate valuation of inventory. To access
it, go to :menuselection:`Accounting --> Review --> Inventory Valuation`. The report includes
the following sections:

- :guilabel:`Initial Balance`: Click to display the stock valuation journal entries.
- :guilabel:`Inventory Loss`: If the :guilabel:`Loss Account` was filled in during
  :ref:`configuration <accounting/inventory-valuation/configuration>`, click to see the list of
  moves to or from the inventory loss locations.
- :guilabel:`Cost of Production`: If the :guilabel:`Cost of Production` account was filled in during
  :ref:`configuration <accounting/inventory-valuation/configuration>`, click to display the stock
  moves associated with manufacturing orders.
- :guilabel:`Stock Variation` displays the difference between the posted inventory value and the
  stock valuation recorded in the Inventory app (i.e., the remaining quantity in stock moves).
- :guilabel:`Ending Stock`: Click to access the :doc:`Inventory Stock
  <../../../inventory_and_mrp/inventory/warehouses_storage/reporting/stock>` report.

.. note::
   Stock variation is automatically recorded with a :ref:`closing entry
   <accounting/inventory-valuation/closing-entry>` at the end of the period set during
   :ref:`configuration <accounting/inventory-valuation/configuration>` or manually when
   :ref:`generating an entry <accounting/inventory-valuation/closing-entry>`.

.. _accounting/inventory-valuation/closing-entry:

Closing entry
-------------

To create an inventory adjustment accounting entry in the :guilabel:`Inventory Valuation` journal
and synchronize accounting records with stock value, follow these steps:

#. Open the :ref:`Inventory Valuation <accounting/inventory-valuation/inventory-valuation-report>`
   report.
#. By default, the closing date is set to the end of the fiscal period. If needed, click
   :icon:`fa-calendar` :guilabel:`As of` to select a different inventory valuation date.
#. Click :guilabel:`Generate Entry`.
#. Review the draft :guilabel:`Stock Closing` entry if needed, and click :guilabel:`Post`.

.. note::
   The :guilabel:`Stock Valuation` and :guilabel:`Stock Variation` accounts are then updated in the
   :ref:`general ledger <accounting/reporting/general-ledger>`.

.. _accounting/inventory-valuation/accrual entries:

Accrual entries
===============

To check for pending transactions requiring accrual entries:

#. Go to :menuselection:`Accounting --> Review` and select the relevant report: :guilabel:`Bill To
   Receive`, :guilabel:`Invoices To Be Issued`, :guilabel:`Billed Not Received`, and
   :guilabel:`Invoiced Not Delivered`.
#. Click :icon:`fa-calendar` :guilabel:`As of` to change the date, if needed.
#. Select the relevant lines and click :guilabel:`Create Accrual Entries`.
#. In the :guilabel:`Accrued Revenue/Expense Entry` window, set the :guilabel:`Accrual Account` and
   review the :guilabel:`Reversal Date`, if needed. Then, click :guilabel:`Create Entry`.

.. _accounting/inventory-valuation/upgrade-process:

Upgrade process
===============

In version 19.0, the stock input/output accounts are no longer used. If these accounts have non-zero
balances, a manual journal entry must be created to transfer the balance from
the interim account to the :ref:`stock valuation account
<accounting/inventory-valuation/valuation-account>`.

This adjustment ensures the inventory account balance remains accurate after migration and keeps
pre-migration accounting entries consistent with the new inventory valuation logic. The adjustment
can be performed either :ref:`before <accounting/inventory-valuation/before-upgrade>` or :ref:`after
<accounting/inventory-valuation/after-upgrade>` upgrading to 19.0.

.. tip::
   It is recommended to apply the change after upgrading to 19.0, as a server action identifies the
   open balance in the :guilabel:`Stock Interim` accounts.

.. important::
   Account structures and valuation scenarios differ across companies. It is recommended to review
   these steps with an accountant or someone experienced with Odoo and inventory valuation to ensure
   they align with the company's specific setup.

.. _accounting/inventory-valuation/before-upgrade:

Before upgrading to 19.0
------------------------

To maintain accurate stock values after migration, rebalance any non-zero account balances by
creating a journal entry:

- Review received purchase/sales orders not yet linked to vendor bills or invoices. Post any
  existing draft bills/invoices to reduce the open balance. Alternatively, clear the open balance
  now and create the accounting documents after upgrading to 19.0.
- Go to :menuselection:`Accounting --> Reporting --> General Ledger`.
- Identify the open balance in the :guilabel:`Stock Interim` accounts and create a journal entry
  that debits/credits:

  - The :guilabel:`Stock Interim` account(s) containing the open balance
  - The :guilabel:`Stock valuation` account

- Check the General Ledger to confirm that the :guilabel:`Stock Interim` accounts are balanced to
  zero and that the remaining amount is recorded in the :guilabel:`Stock valuation` account.

The stock valuation is now ready to be upgraded to 19.0.

.. _accounting/inventory-valuation/after-upgrade:

After upgrading to 19.0
-----------------------

.. important::
   Since this action is generic, it is important to verify that the amounts generated by the server
   action match the remaining balances. It's recommended to use a testing database created during
   the upgrade process.

The server action must be applied per company to balance any non-zero :guilabel:`Stock Interim`
accounts:

- Go to :menuselection:`Settings --> Users & Companies --> Companies` and access the company form.
- Click the :icon:`fa-cog` :guilabel:`(gear)` icon and select :guilabel:`Stock Valuation rebalance
  interim Accounts`. A draft journal entry is automatically generated to balance the open amount.
- Review the draft journal entry amounts, then click :guilabel:`Post`.

The remaining amount is then recorded in the :guilabel:`Stock valuation` account.

.. note::
   Journal entries can also be created manually if needed, using the same process for balancing
   :guilabel:`Stock Interim` accounts :ref:`before upgrading to 19.0
   <accounting/inventory-valuation/before-upgrade>`.

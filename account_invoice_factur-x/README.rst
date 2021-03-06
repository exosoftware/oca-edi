.. image:: https://img.shields.io/badge/licence-AGPL--3-blue.svg
   :target: http://www.gnu.org/licenses/agpl-3.0-standalone.html
   :alt: License: AGPL-3

========================
Account Invoice Factur-X
========================

With this module, the PDF customer invoices and refunds generated by the Qweb reporting engine of Odoo will comply with the `Factur-X <http://fnfe-mpe.org/factur-x/>`_ standard at *EN 16931* level. The Factur-X standard is the new e-invoicing standard for France and Germany released in Beta version in July 2017. In Germany, it is also known as the `ZUGFeRD 2.0 <http://www.ferd-net.de/aktuelles/meldungen/verabschiedung-zugferd-2.0_profil-en16931.html/>`_ standard. This standard is based on `CII <http://tfig.unece.org/contents/cross-industry-invoice-cii.htm>`_ (Cross-Industry Invoice) for electronic invoicing. The great idea of the ZUGFeRD/Factur-X standard is to embed an XML file inside the PDF invoice to carry structured information about the invoice. So, with a ZUGFeRD/Factur-X PDF invoice:

* no need to change your habbits and those of your customers: you can still send your PDF invoices by email as usual.
* customers equiped with a modern accouting software will be able to import the invoice automatically as supplier invoice by taking advantage of the embedded XML file,
* customers with an ancient accounting software will just open the PDF file with their PDF reader and manually encode the document as supplier invoice in their accounting software.

Installation
============

This module requires the Python library *factur-x* with **version >= 0.3** developped by Akretion. Note that the factur-x library depends on PyPDF2 for the low-level PDF manipulation. To install it, run:

.. code::

  sudo pip install factur-x

Configuration
=============

In the menu *Accounting > Configuration > Settings*, check these options:

* *XML Format embedded in PDF invoice*: if you want to generate Factur-X invoices, this option must be set to *Factur-X (CII)*
* the *Factur-X Level*: unless you have a good reason, you should keep the default value *EN 16931 (Comfort)*
* *Factur-X Refund Type*: choose the type of the XML invoice for customer refunds.

Usage
=====

On the form view of a customer invoice/refund, just click on the *Print* button as usual to get the Factur-X-compliant PDF file.

.. image:: https://odoo-community.org/website/image/ir.attachment/5784_f2813bd/datas
   :alt: Try me on Runbot
   :target: https://runbot.odoo-community.org/runbot/226/10.0

Known issues / Roadmap
======================

* for Odoo v11, use the new hooks in the report code to embed the XML file inside the PDF file just after its generation and before it is saved as attachment.

* develop glue modules (or use hasattr() ?) to add to the XML file pieces of information that is carried out by fields defined in other modules such as sale or stock (customer order reference, incoterms, delivery address, etc...).

Bug Tracker
===========

Bugs are tracked on `GitHub Issues
<https://github.com/OCA/edi/issues>`_. In case of trouble, please
check there if your issue has already been reported. If you spotted it first,
help us smashing it by providing a detailed and welcomed feedback.

Credits
=======

Contributors
------------

* Alexis de Lattre <alexis.delattre@akretion.com>

Maintainer
----------

.. image:: https://odoo-community.org/logo.png
   :alt: Odoo Community Association
   :target: https://odoo-community.org

This module is maintained by the OCA.

OCA, or the Odoo Community Association, is a nonprofit organization whose
mission is to support the collaborative development of Odoo features and
promote its widespread use.

To contribute to this module, please visit https://odoo-community.org.

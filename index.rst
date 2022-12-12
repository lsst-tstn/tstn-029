..
  Technote content.

  See https://developer.lsst.io/restructuredtext/style.html
  for a guide to reStructuredText writing.

  Do not put the title, authors or other metadata in this document;
  those are automatically added.

  Use the following syntax for sections:

  Sections
  ========

  and

  Subsections
  -----------

  and

  Subsubsections
  ^^^^^^^^^^^^^^

  To add images, add the image file (png, svg or jpeg preferred) to the
  _static/ directory. The reST syntax for adding the image is

  .. figure:: /_static/filename.ext
     :name: fig-label

     Caption text.

   Run: ``make html`` and ``open _build/html/index.html`` to preview your work.
   See the README at https://github.com/lsst-sqre/lsst-technote-bootstrap or
   this repo's README for more info.

   Feel free to delete this instructional comment.

:tocdepth: 1

.. Please do not modify tocdepth; will be fixed when a new Sphinx theme is shipped.

.. sectnum::

.. TODO: Delete the note below before merging new content to the main branch.

.. note::

   **This technote is in rough draft.**

   TBD


Introduction
============
The Engineering Facility Database (EFD) has a requirement to support objects that are too large or unwieldy for regular SAL commands, events and telemetry.
The Large File Annex (LFA) is the solution to this requirement.
The LFA uses Amazon's Simple Storage Service (S3) to store these objects.


Architecture
============
The LFA uses Amazon's S3 to store objects.
S3 uses the concept of buckets to organize objects.
Conceptually for the LFA, buckets correspond to sites i.e. Tucson Test Stand, Summit, Base Test Stand.
Bucket names have the following format `rubinobs-{s3category}-{s3instance}`.
s3category refers to the category of bucket, currently there is only LFA defined.
s3instance refers to the site name.

* tuc - tucson
* cp - summit
* ls - base

Each object (file) uploaded to a bucket must have a key (name) that follows the Vera C. Rubin standard.
The key format is `{fullsalname}/{generator}/{yyyy}/{mm}/{dd}/{fullsalname}-{generator}-{other}{suffix}`

:fullsalname: Refers to full CSC name including index name if exists `{salname}:{salindexname}`.
:generator: metadata that outlines where the object was generated i.e. FiberSpectrograph using different filters
:yyyy-mm-dd: Refers to the observing day, which does not turnover during the night observing.
:other: Extra metadata
:suffix: object extension i.e. fits

Client Support
==============
`Adding LFA support using salobj <https://ts-salobj.lsst.io/salobj_cscs.html#large-file-annex-writer>`_

.. Add content here.
.. Do not include the document title (it's automatically added from metadata.yaml).

.. .. rubric:: References

.. Make in-text citations with: :cite:`bibkey`.

.. .. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
..    :style: lsst_aa

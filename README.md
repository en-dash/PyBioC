# PyBioC

**[PyBioC][1] is a native Python library for reading and writing BioC XML data.**

More information about BioC is available at [sourceforge][2].


## Installation

Use [`pip`][3]:

    pip install git+https://github.com/OntoGene/PyBioC.git

For Python 3, you might have to type `pip3`.


## Usage

Two example programs, test_read+write.py and stemming.py are shipped in the `src/` folder.

- `test_read+write.py` shows the very
basic reading and writing capability
of the  library.
- `stemming.py` uses the Python Natural
Language Toolkit (NLTK) library to
manipulate a BioC XML file read in
before; it then tokenizes the
corresponding text, does stemming on
the tokens and transforms the
manipulated PyBioC objects back to
valid BioC XML format.


## Example

### Generate BioC object for export

```python
from bioc import BioCXMLWriter, BioCCollection, BioCDocument, BioCPassage

writer = BioCXMLWriter()
writer.collection = BioCCollection()
collection = writer.collection
collection.date = '20150301'
collection.source = 'ngy1 corpus'

document = BioCDocument()
document.id = '123456'  # pubmed id

passage = BioCPassage()
passage.put_infon('type', 'paragraph')
passage.offset = '0'
passage.text = 'This is a biomedical sentence about various rare diseases.'
document.add_passage(passage)

collection.add_document(document)

print writer
```



[1]: https://github.com/OntoGene/PyBioC
[2]: http://bioc.sourceforge.net/
[3]: http://pip.pypa.io/

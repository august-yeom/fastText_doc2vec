# fastText_doc2vec

fastText_doc2vec is an extension of the [Facebook fastText](https://github.com/facebookresearch/fastText) for document embedding. 

## Requirements

**fastText_doc2vec** builds on similar environment of [Facebook fastText](https://github.com/facebookresearch/fastText#requirements).

## Building fastText 

In order to build `fastText_doc2vec`, use the following:

```
$ git clone https://github.com/Skarface-/fastText_doc2vec.git
$ cd fastText_doc2vec
$ make
```

This will produce object files for all the classes as well as the main binary `fasttext`. <br/> If you do not plan on using the default system-wide compiler, update the two macros defined at the beginning of the Makefile (CC and INCLUDES).

## Example use cases

This library has two use cases: document embedding using PV-DM and PV-DBOW model. <br/> 
These were described in the paper [1](#distributed-representations-of-sentences-and-documents).

### Document Embedding

In order to embed document in vector space, as described in [1](#distributed-representations-of-sentences-and-documents), do:

```
$ ./fasttext pvdm -model model.bin -input data.txt -output docvecs
or
$ ./fasttext pvdbow -model model.bin -input data.txt -output docvecs
```

where `model.bin` is a previously trained model using [fasttext word representation learning](https://github.com/facebookresearch/fastText#word-representation-learning). <br/> 
As such, most options are inherited from [fasttext word representation learning](https://github.com/facebookresearch/fastText#word-representation-learning) without epoch, thread, [etc](#full-documentation) <br/> 
`data.txt` is a file containing `utf-8` encoded labeled documents. (\_\_label\_\_\<label\>, \<text\>) <br/> 
At the end of document embeding, the program will save a single file: `docvecs.vec`. <br/> 
`docvecs.vec` is a text file containing the labeled document vectors, one per line. 

## Full documentation

Invoke a command without arguments to list available arguments and their default values:

```
$ ./fasttext pvdm
Empty model or input or output path.

The following arguments are mandatory:
  -model      (mandatory, only pvdm or pvdbow) model.bin file path for document embedding
  -input      training file path
  -output     output file path

The following arguments are optional:
  -lr         learning rate [0.05]
  -epoch      number of epochs [5]
  -thread     number of threads [12]
  -verbose    how often to print to stdout [10000]
  -label      labels prefix [__label__]
```

## References

Please cite [1](#distributed-representations-of-sentences-and-documents) and [2](#enriching-word-vectors-with-subword-information).

### Distributed Representations of Sentences and Documents

[1] Quoc V. Le, T. Mikolov, [*Distributed Representations Of Sentences And Documents*](https://arxiv.org/abs/1405.4053v2)

```
@article{quoc2014distributed,
  title={Distributed Representations of Sentences and Documents},
  author={Le, Quoc V. and Mikolov, Tomas},
  journal={arXiv preprint arXiv:1405.4053v2},
  year={2014}
}
```

### Enriching Word Vectors with Subword Information

[2] P. Bojanowski\*, E. Grave\*, A. Joulin, T. Mikolov, [*Enriching Word Vectors with Subword Information*](https://arxiv.org/pdf/1607.04606v1.pdf)

```
@article{bojanowski2016enriching,
  title={Enriching Word Vectors with Subword Information},
  author={Bojanowski, Piotr and Grave, Edouard and Joulin, Armand and Mikolov, Tomas},
  journal={arXiv preprint arXiv:1607.04606},
  year={2016}
}
```

## The fastText community

* Facebook page: https://www.facebook.com/groups/1174547215919768
* Google group: https://groups.google.com/forum/#!forum/fasttext-library

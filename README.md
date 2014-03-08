MeCab English Documentation
===========================

This is based on the [MeCab documentation](http://mecab.googlecode.com/svn/trunk/mecab/doc/index.html).

What is MeCab?
--------------

MeCab is an open source morphological analysis engine developed as a joint research
project between Kyoto University Information Research
department and the Nippon Telegraph and Telecommunications Communication Science
Laboratories. It is built with the goal of general purpose analysis and
does not depend on any particular language corpus/dictionary. 

MeCab uses Conditional Random Fields (CRF) parameter estimation, improving upon
the Hidden Markov Models as used by ChaSen. MeCab also typically performs faster
than ChaSen, Juman, and KAKASI. Incidentally, mekabu is the author's favourite dish.

(Translator's note: MeCab in Japanese is pronounced 'mekabu' - which is the thick
part of wakame seaweed just above the root)

Features
--------
 - Generic design that does not depend on a dictionary corpus
 - Based on Conditional Random Fields (CRF) for high precision analysis
 - Faster than ChaSen and KAKASI libraries
 - Dictionary search algorithm uses high speed TRIE structure double-array
 - Library is re-entrant
 - Bindings for various scripting languages (Perl, Ruby, Python, Java, C#)

Comparison
----------

(Todo)

Mailing List
------------

Changelog
---------
(Todo)

Downloads
---------


Installation
------------

### Unix

#### Requirements
 - C++ compiler (compiles with g++ 3.4.3 and VC7)

#### MeCab Installation

Installation is the same as typical free software.

    % tar zxfv mecab-X.X.tar.gz
    % cd mecab-X.X
    % ./configure
    % make
    % make check
    % su
    # make install

#### Dictionary installation

    % tar zxfv mecab-ipadic-2.7.0-XXXX.tar.gz
    % mecab-ipadic-2.7.0-XXXX
    % ./configure
    % make
    % su
    # make install

### Windows


めかぶ

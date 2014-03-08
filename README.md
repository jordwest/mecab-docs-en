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

(TODO)

Mailing List
------------

Changelog
---------
(TODO)

Downloads
---------
[See project page for up to date downloads](http://mecab.googlecode.com/svn/trunk/mecab/doc/index.html#download)

Installation
------------

### Unix

#### Requirements
 - C++ compiler (compiles with g++ 3.4.3 and VC7)
 - iconv (libiconv): used for dictionary format conversion

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

For binary installation, please use the self-extracting installer. Do the same 
for dictionary installation.

Usage
-----

### Getting Started

See below MeCab accepting input from stdin upon startup. MeCab assumes one line
per sentence.

    % mecab
    すもももももももものうち
    すもも  名詞,一般,*,*,*,*,すもも,スモモ,スモモ
    も      助詞,係助詞,*,*,*,*,も,モ,モ
    もも    名詞,一般,*,*,*,*,もも,モモ,モモ
    も      助詞,係助詞,*,*,*,*,も,モ,モ
    もも    名詞,一般,*,*,*,*,もも,モモ,モモ
    の      助詞,連体化,*,*,*,*,の,ノ,ノ
    うち    名詞,非自立,副詞可能,*,*,*,うち,ウチ,ウチ
    EOS

The output format significantly differs from ChaSen, becoming:

    表層形\t品詞,品詞細分類1,品詞細分類2,品詞細分類3,活用形,活用型,原形,読み,発音

or in English:

    Original Form\t
    Part of Speech,
    Part of Speech section 1,
    Part of Speech section 2,
    Part of Speech section 3,
    Conjugated form,
    Inflection,
    Reading,
    Pronounciation

If a file is passed in as the argument, it becomes the analysis target.
It is also possible to direct output to a file using the -o option. 

    % mecab INPUT -o OUTPUT

### Division

Use the -O option as below

    % mecab -O wakati
    太郎はこの本を二郎を見た女性に渡した。
    太郎 は この 本 を 二郎 を 見 た 女性 に 渡し た 。

### Change output format

Use the -O option as below

    % mecab -Oyomi (ヨミ付与)
    % mecab -Ochasen (ChaSen互換)
    % mecab -Odump (全情報を出力)

These output formats are stored in `/usr/local/lib/mecab/ipadic/dicrc`.
The user can also create custom definitions. Please take a look
at the Output Formats documentation (TODO).

Advanced Usage
--------------
### Changing the character code

(TODO)

    % tar zxfv mecab-ipadic-2.7.0-xxxx
    % cd mecab-ipadic-2.7.0-xxxx
    % ./configure --with-charset=sjis
    % make
    
    % tar zxfv mecab-ipadic-2.7.0-xxxx
    % ./configure --with-charset=utf8
    % make

(TODO)

    % cd mecab-ipadic-2.7.0-xxxx
    % /usr/local/libexec/mecab/mecab-dict-index -f euc-jp -t utf-8
    # make install

### UTF-8 only mode

(TODO)

### Unknown Word Estimation

(TODO)

    ホリエモン市
    ホリエモン      名詞,固有名詞,地域,一般,*,*,*
    市      名詞,接尾,地域,*,*,*,市,シ,シ
    EOS
    ホリエモンさん
    ホリエモン      名詞,固有名詞,人名,一般,*,*,*
    さん    名詞,接尾,人名,*,*,*,さん,サン,サン

(TODO)

    %mecab --unk-feature "未知語" 
    ホリエモンさん
    ホリエモン      未知語
    さん    名詞,接尾,人名,*,*,*,さん,サン,サン

### N-Best Solution Output

(TODO)

    % mecab -N2
    今日もしないとね。
    今日    名詞,副詞可能,*,*,*,*,今日,キョウ,キョー
    も      助詞,係助詞,*,*,*,*,も,モ,モ
    し      動詞,自立,*,*,サ変・スル,未然形,する,シ,シ
    ない    助動詞,*,*,*,特殊・ナイ,基本形,ない,ナイ,ナイ
    と      助詞,接続助詞,*,*,*,*,と,ト,ト
    ね      助詞,終助詞,*,*,*,*,ね,ネ,ネ
    。      記号,句点,*,*,*,*,。,。,。
    EOS
    今日    名詞,副詞可能,*,*,*,*,今日,キョウ,キョー
    もし    副詞,一般,*,*,*,*,もし,モシ,モシ
    ない    形容詞,自立,*,*,形容詞・アウオ段,基本形,ない,ナイ,ナイ
    と      助詞,接続助詞,*,*,*,*,と,ト,ト
    ね      助詞,終助詞,*,*,*,*,ね,ネ,ネ
    。      記号,句点,*,*,*,*,。,。,。
    EOS

Acknowledgements
----------------

Jorge Nocedal for making the FORTRAN implementation of L-BFGS open to the public.

[http://www.ece.northwestern.edu/~nocedal/lbfgs.html](http://www.ece.northwestern.edu/~nocedal/lbfgs.html)

J. Nocedal. Updating Quasi-Newton Matrices with Limited Storage (1980), Mathematics of Computation 35, pp. 773-782.
D.C. Liu and J. Nocedal. On the Limited Memory Method for Large Scale Optimization (1989), Mathematical Programming B, 45, 3, pp. 503-528.

めかぶ

# Huffman Coding

The code can be used for study, and as a solid basis for modification 
and extension. Consequently, the codebase optimizes for readability 
and avoids fancy logic, and does not target the best speed/memory/performance.

Home page with detailed description:
 https://www.nayuki.io/page/reference-huffman-coding

## Overview

Huffman encoding takes a sequence (stream) of symbols as input and gives
a sequence of bits as output. The intent is to produce a short output for 
the given input. Each input yields a different output, so the process can
be reversed, and the output can be decoded to give back the original input.

In this software, a symbol is a non-negative integer. The symbol limit is
one plus the highest allowed symbol. For example, a symbol limit of 4 means
that the set of allowed symbols is {0, 1, 2, 3}.

## Submodules

### Sample Applications

Two pairs of command-line programs fully demonstrate how this software 
package can be used to encode and decode data using Huffman coding. One 
pair of programs is the classes HuffmanCompress and HuffmanDecompress, 
which implement static Huffman coding. The other pair of programs is the 
classes AdaptiveHuffmanCompress and AdaptiveHuffmanDecompress, which 
implement adaptive/dynamic Huffman coding.

### Encoder/Decoder

The classes HuffmanEncoder and HuffmanDecoder implement the basic 
algorithms for encoding and decoding a Huffman-coded stream. The code
tree must be set before encoding or decoding. The code tree can be 
changed after encoding or decoding each symbol, as long as the encoder
and decoder have the same code tree at the same position in the symbol
stream. At any given time, the encoder must not attempt to encode a
symbol that is not in the code tree.

### Huffman Code Tree

The class CodeTree, along with Node, InternalNode, and Leaf, represent
a Huffman code tree. The leaves represent symbols. The path to a leaf
represents the bit string of its Huffman code.

<p align="center">
    <img src="/Documentation/Code-Tree-Model.svg" alt="Code Tree" 
        height="300px"/>
</p>

### Frequency Table

The class FrequencyTable wraps over a simple integer array to count
symbol frequencies. It is also responsible for generating a Huffman 
code tree that is optimal for its current array of frequencies (but 
not necessarily canonical).

### Canonical Codes

The class CanonicalCode converts an arbitrary CodeTree to a canonical
code. It can then generate a CodeTree for the canonical code.

### Bitwise I/O Streams

The classes BitInputStream and BitOutputStream are bit-oriented I/O
streams, analogous to the standard bytewise I/O streams. However, 
since they use an underlying bytewise I/O stream, the bit stream’s 
total length is always a multiple of 8 bits.


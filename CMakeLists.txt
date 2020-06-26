CMAKE_MINIMUM_REQUIRED(VERSION 3.16)
PROJECT(cpp)

SET(CMAKE_CXX_STANDARD 14)

ADD_LIBRARY(Huffman.Code BitIoStream.cpp CanonicalCode.cpp CodeTree.cpp FrequencyTable.cpp HuffmanCoder.cpp)

ADD_EXECUTABLE(Huffman.Compress HuffmanCompress.cpp)
TARGET_LINK_LIBRARIES(Huffman.Compress PRIVATE Huffman.Code)

ADD_EXECUTABLE(Huffman.Decompress HuffmanDecompress.cpp)
TARGET_LINK_LIBRARIES(Huffman.Decompress PRIVATE Huffman.Code)

ADD_EXECUTABLE(Adaptive.Huffman.Compress AdaptiveHuffmanCompress.cpp)
TARGET_LINK_LIBRARIES(Adaptive.Huffman.Compress PRIVATE Huffman.Code)

ADD_EXECUTABLE(Adaptive.Huffman.Decompress AdaptiveHuffmanDecompress.cpp)
TARGET_LINK_LIBRARIES(Adaptive.Huffman.Decompress PRIVATE Huffman.Code)
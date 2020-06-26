CMAKE_MINIMUM_REQUIRED(VERSION 3.1 FATAL_ERROR)
PROJECT(Huffman.Coding LANGUAGES CXX)

ADD_LIBRARY(Huffman.Coding BitIoStream.cpp CanonicalCode.cpp CodeTree.cpp FrequencyTable.cpp HuffmanCoder.cpp)
SET_TARGET_PROPERTIES(Huffman.Coding PROPERTIES CXX_STANDARD 17)
TARGET_INCLUDE_DIRECTORIES(Huffman.Coding PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/Include/>
        $<INSTALL_INTERFACE:Include/>)

ADD_EXECUTABLE(Huffman.Compress HuffmanCompress.cpp)
SET_TARGET_PROPERTIES(Huffman.Compress PROPERTIES CXX_STANDARD 17)
TARGET_LINK_LIBRARIES(Huffman.Compress PRIVATE Huffman.Coding)

ADD_EXECUTABLE(Huffman.Decompress HuffmanDecompress.cpp)
SET_TARGET_PROPERTIES(Huffman.Decompress PROPERTIES CXX_STANDARD 17)
TARGET_LINK_LIBRARIES(Huffman.Decompress PRIVATE Huffman.Coding)

ADD_EXECUTABLE(Adaptive.Huffman.Compress AdaptiveHuffmanCompress.cpp)
SET_TARGET_PROPERTIES(Adaptive.Huffman.Compress PROPERTIES CXX_STANDARD 17)
TARGET_LINK_LIBRARIES(Adaptive.Huffman.Compress PRIVATE Huffman.Coding)

ADD_EXECUTABLE(Adaptive.Huffman.Decompress AdaptiveHuffmanDecompress.cpp)
SET_TARGET_PROPERTIES(Adaptive.Huffman.Decompress PROPERTIES CXX_STANDARD 17)
TARGET_LINK_LIBRARIES(Adaptive.Huffman.Decompress PRIVATE Huffman.Coding)

# Introduction to Unicode standard

## History: ASCII

Before Unicode appeared, coding used __ASCII__, a transformation of bytes into letters, combined of 7 bits from 0000000 to 1111111: with numbers 0 and 1. It was divided into octets (or 8 bits) where 1 byte equal 1 letter. For example, in that system 01000001 means A.

__ASCII__ Table includes

- 95 symbols from A to Z (all registers);
- numbers from 0 to 9;
- popular punctuation symbols;
- 33 symbols like as tab or space.

__ASCII__ can use a null bit to add 128 more values. It is still not enough for languages with umlauts or picture characters.

![ASCII](http://www.lo8.poznan.pl/belferek/klasa1/budkom/ascii.gif)

## Multi-byte character sets
These character sets have more values in their table, because they include segments of 16 bits. That makes more than 65536 values. For example, __Big-5__ could contain symbols of traditional Chinese, while __GB18030__ contained both the symbols of traditional Chinese and its simplified version.

A line without specific encoding may not be displayed correctly and it presents a pseudo graphic symbol. This is why it is necessary to know which character set is used. In the course of time,  character sets grew too numerous, and using various character sets on PC became problematic. Unicode Consortium decided to develop a universal standard.

## Unicode
This is not a  character set, but rather a  standard of encoding for graphic symbols in a table of 1 114 112 items.

![Unicode](https://i.pinimg.com/736x/4b/6b/ea/4b6bea592021af3bf523cd69a59733e2.jpg)

It was no longer necessary to switch code pages, because the function was already included in the Unicode standard. Unicode contains the data for all languages, including prehistoric, exotic and fictitious ones.

You can search __Unicode Character Database__ as text/XML in the [official site](https://unicode.org). 12.1 is the current version of Unicode, updated in May 2019. Updates do not offer new symbols, instead Unicode Consortium adds symbols into the Character Database. Symbols like emoji (for example, :smile: or :sleeping:) were added at some point, because they have become very wide-spread.

### How does Unicode mark symbols?
It uses Unicode items in a hexadecimal system, which is included into __UCS__ character sets. But character codes aren’t values of 16 bits, they are abstract numbers for representation. A character code his preceded by a prefix «U+». For example, it may look like «U+1E00».

The Unicode Table has sections, where the first part includes symbols of __ASCII__, with other parts including punctuation symbols, specific symbols of other languages, and there is even some space for potential symbols to be added in the future. Symbols may be presented by different codes: a letter may be an individual character or a combination of characters. Normalization algorithms transform characters into standard forms by decomposition or composition.

### How are codes transformed into bits?
__UTF__-encoding is used to mark ways of symbol codes transformation for transmission in files or a data stream. 2 bytes aren’t enough for encoding 1 114 112 symbols. But 4 bytes aren’t effective when you use languages without thousands of characters, for example, English, which includes a small range of symbols that is served well enough by __ASCII__. As a result, Unicode developed character sets with variable length encoding: __UTF-8__ и __UTF-16__.

## UTF-8
This character set uses a minimal character equal to 1 byte: it encodes a character by 1 byte, if it needs 1 byte, it encodes a character by 2 bytes, if it needs 2 bytes. It follows this principle of encoding up to 4 bytes. This approach saves memory, but it may use more memory, if such decryption is used often. __UTF-8__ is compatible with __ASCII__.

UTF-8 uses a signature (__BOM__) to mark the byte order, but you may save files in UTF-8 without __BOM__. Windows programs present it as bytes 0xFF, 0xBB, 0xBF. Incidentally, UTF-8 hasn’t 0xFE and 0xFF: it may be used for identification of UTF-16.

## UTF-16
This character set uses minimal characters equal to 2 bytes and encoding up to 4 bytes, if it is necessary to represent symbols. The first 65 535 symbols are represented by means of 2 bytes, other symbols are represented by means of 4 bytes. This character set includes 1 114 112 Unicode symbols.

Application
UTF-8 is used in GNU/Linux, BSD, MacOS X and is common  for web pages. UTF-16 is divided into __UTF-16BE__ и __UTF-16-LE__. Little Endian is applied in Windows, Big Endian is applied in *NIX OC.

Symbol data are represented by __wchar_t__. You may indicate a character set in the setting of projects in Microsoft Visual Studio and in the block «header» at a  web page. Unicode was first used in __Java__.

## Pros and cons of UTF-8 and UTF-16
1. UTF-8 has better compatibility with older systems: a text encoded in UTF-8 can be transformed into ASCII. If the program can not recognize Unicode, ASCII characters are displayed correctly with the UTF-8 character set, and you may use UTF-8 as an old character set. But old programs can not process files with the UTF-16 character set.

2. When you need a minimal set of symbols, UTF-8 encodes a character by means of 1 byte, UTF-16 encodes a character by means of 2 bytes, so UTF-8 is the winner in the battle for memory, especially if you use symbols of ASCII in the biggest part of the text. UTF-16 has more symbols.

3. UTF-16 has to indicate the byte order, but UTF-8 has an indication of the byte order by default. UTF-8 also processes errors better than UTF-16.

***

So, if your product is aimed at an English-speaking market, you would tend to __prefer UTF-8__ with its effective memory usage and backward compatibility. But if you need representation of various writing systems and the memory sources are not harshly limited, you would normally __prefer UTF-16__ as a more universal system with more characters.















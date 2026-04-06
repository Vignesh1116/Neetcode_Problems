<!-- Design an algorithm to encode a list of strings to a string. The encoded string is then sent over the network and is decoded back to the original list of strings.

Machine 1 (sender) has the function:

string encode(vector<string> strs) {
    // ... your code
    return encoded_string;
}
Machine 2 (receiver) has the function:

vector<string> decode(string s) {
    //... your code
    return strs;
}
So Machine 1 does:

string encoded_string = encode(strs);
and Machine 2 does:

vector<string> strs2 = decode(encoded_string);
strs2 in Machine 2 should be the same as strs in Machine 1.

Implement the encode and decode methods.

Example 1:

Input: dummy_input = ["Hello","World"]

Output: ["Hello","World"]

Explanation:
Machine 1:
Codec encoder = new Codec();
String msg = encoder.encode(strs);
Machine 1 ---msg---> Machine 2

Machine 2:
Codec decoder = new Codec();
String[] strs = decoder.decode(msg); -->

class Solution:

    def encode(self, strs: List[str]) -> str:
        if not strs:
            return ""
        sizes , result = [], ""
        for word in strs:
            sizes.append(len(word))#[]
        for lengths in sizes:
            result += str(lengths)
            result += "," 
        result += "#"  #   "4,4,4,3,#""
        for words in strs:
            result += words
        return result #   "4,4,4,3,#neetcodeloveyou"

    def decode(self, s: str) -> List[str]:
        if not s:#""
            return []
        sizes, result, i = [], [], 0
        while s[i] != "#" : #3
            hashcut = "" #""
            while s[i] != ",":
                hashcut += s[i] #"3"
                i += 1
            sizes.append(int(hashcut)) #[4,4,4,3]
            i += 1 #8
        i += 1 # 9
        for size in sizes: #4
            result.append(s[i:i+size])#s[13:13+4] code
            i += size #13
        return result
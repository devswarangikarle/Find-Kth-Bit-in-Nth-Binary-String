# Find-Kth-Bit-in-Nth-Binary-String

Given two positive integers n and k, the binary string Sn is formed as follows:

S1 = "0"
Si = Si - 1 + "1" + reverse(invert(Si - 1)) for i > 1
Where + denotes the concatenation operation, reverse(x) returns the reversed string x, and invert(x) inverts all the bits in x (0 changes to 1 and 1 changes to 0).

For example, the first four strings in the above sequence are:

S1 = "0"
S2 = "011"
S3 = "0111001"
S4 = "011100110110001"
Return the kth bit in Sn. It is guaranteed that k is valid for the given n.

class Solution:

    def findKthBit(self, n: int, k: int) -> str:
        bits = '0'
        for _ in range(n - 1):
            newBits = '1'
            size = len(bits)
            for i in range(size - 1, -1, -1):
                newBits += ('0' if bits[i] == '1' else '1')
            bits += newBits

        return bits[k - 1]

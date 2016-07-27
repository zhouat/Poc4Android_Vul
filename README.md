# Practical Tools

[1]convert text to binary, eq to xxd -r -p

import struct

infile = open("data","rb")
outfile = open("out.txt","wb")

def main():
	buf=['','']
	index=0
	line = infile.read(1)
	while line:
		if line != '\n':
			buf[index]=line
			index=(index+1)%2
			if(index%2==0):
				#print ''.join(buf)
				#B unsigned char integer 1Byte
				outfile.write(struct.pack('B',int(''.join(buf),16)))
		line =  infile.read(1)
if __name__ == '__main__':
	main()

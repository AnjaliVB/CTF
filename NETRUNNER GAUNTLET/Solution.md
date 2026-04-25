OSINT 
ROAM THE WORLD
Methodology:
1st hint: Behold Hacker, You have stepped into the realm of cybernois. To enter further you have to find the secret key The secret key belongs to Indian CEO of a BIG company. He studied in an IIT. Tell me the year he was born to get the secret key.
Result-1972 (Sundar Pichai)
This unlocked secrert.zip. it had message.txt
The solution to this abyss is easier to find only if you are willing to search. As you know this is conducted by CEG TECH FORUM, the secret to the file is hash of the name of the Student Director whose starting letter is p. So find out who he is?
Result-ad8749cba3fe6de1ef4d942ab1f55f1c
(purushothaman- checked the whatsapp grp)
This opened challenge.zip. it had Message.zip which contained message.txt.
Message.txt: O my goodness, You have reached near but to unlock the mystery you will need to say the magic word to the zip wizard. The answer he seeks belongs to the color of our college building that is very old as you great-great grandfather. But mischievous wizard wants the key in a hash output so give him the hash of the answer to unlock.
Result: bda9643ac6601722a28f238714274da4
(Red color)
This opened another message.txt which had the flag.
CTF{Inf0_is_wealth_rytgbhk76}
Catch Me if you can
Downloaded the image file, viewed the metadata and found this:
Q1RGe2RhdGFfaDFkZGVuXzFuX21ldGFkYXRhfQ==
decoded using base64 by using cyberchef and got: 
CTF{data_h1dden_1n_metadata}
Weird File
Downloaded the .docm file, remaned it with .zip 
opened vbaProject  from “word” folder and got this: Q1RGe21hY3Jvc19hcmVfdGhlX21hY2Fyb25pfQ==
decoded with base64 and got the flag: 
CTF{macros_are_the_macaroni}
Corrupted File
Opened the .bin file and found this header:
%Bin-1.6
%öäüß
Replaced %Bin-1.6 with %PDF-1.6 and renamed the .bin file with .pdf. opened the pdf and got: CTF{hidden_in_plainsight_djbh67jn}

Encoding
enc = "䍔䙻獴物湧彥湣潤敟ⅳ彦畮㙧祴㜷㜸桟桪橽"
script:
flag = ''.join([chr((ord(c) >> 8) & 0xFF) + chr(ord(c) & 0xFF) for c in enc])
print(flag)
flag= CTF{string_encode_!s_fun6gyt7778h_hjj}
Hidden Flag Hunt
4354467b68316464336e5f316e5f347474723162757433737d
decoded this using hex decoder and got :
CTF{h1dd3n_1n_4ttr1but3s}
Cookie Crumbs
Got this session id: Q1RGe2MwMGsxM3NfYXIzX2Ywcl9oNGNrM3JzfQ==
decoded with base64 and got: CTF{c00k13s_ar3_f0r_h4ck3rs}
Interencdec
VUVkVGUzQjFibUYwY2w5bmRYSmZlblpoY1Y5bllsOW9ZWGxpY0hoZlozVnlYMjlsYmpGaGZRPT0=
applied base64 decoding twice and then ROT13 and found the flag: CTF{change_the_mind_to_unlock_the_bra1n}
Picture Mania
from PIL import Image
import numpy as np
img1 = Image.open("share1.png")
img2 = Image.open("share2.png")
a = np.array(img1)
b = np.array(img2)
xor = a ^ b
result = Image.fromarray(xor)
result.save("result.png")

this code xor’s the images and found the flag: CTF{Picture_in_p1c3}

Dachshund Attacks

from fractions import Fraction
from math import isqrt
e = 140873308542427677531290526318240718264930938822683559883608095044731988141718123683236301175041378400304688805500514340100757113035607817931321720472854462802424458019679012984909723409411809729589192422086401736731304634702086576767274750378253430657783726557212129371956661018157175991720551659018781650081

n = 167670193544040228532135953080954230474884575252690447974053917615236340862037878801927744792813463253531559910032544728810962932331088492703951789643125077980961558370652410891851786644378385278289850053751518885921068850116390941780818178779442424918458089453423813932741407801966989122414735318362254344851

c = 74741556653441154536720922690678607903320175672002155755316162197099330095387414342093385791975908986382588256805732649312690304315464736599778128803655969651713346148088190836676324612744845311055921572923999377436470183401996123435314628977025630983615075091387029935901676520338857383484784955190241875829


def continued_fraction(numerator, denominator):
    while denominator:
        a = numerator // denominator
        yield a
        numerator, denominator = denominator, numerator - a * denominator


def convergents(cf):
    convs = []
    for i in range(len(cf)):
        frac = Fraction(0)
        for a in reversed(cf[:i+1]):
            if frac.numerator == 0:
                frac = Fraction(a, 1)
            else:
                frac = 1/frac
                frac += a
        convs.append((frac.numerator, frac.denominator))
    return convs


cf = list(continued_fraction(e, n))
convs = convergents(cf)

d = None
for k, d_candidate in convs:
    if k == 0:
        continue
    if (e * d_candidate - 1) % k != 0:
        continue

    phi_candidate = (e * d_candidate - 1) // k
    s = n - phi_candidate + 1
    discr = s*s - 4*n

    if discr >= 0:
        t = isqrt(discr)
        if t*t == discr:
            p = (s + t) // 2
            q = (s - t) // 2
            if p*q == n:
                d = d_candidate
                break

if d is None:
    print("Not vulnerable to Wiener's attack.")
else:
    print("Private key d found!")
    m = pow(c, d, n)
    print("Decrypted integer:", m)

    # Convert to readable text if possible
    try:
        plaintext = bytes.fromhex(hex(m)[2:]).decode()
        print("Plaintext:", plaintext)
    except:
        print("Raw hex:", hex(m))

Rain down the Music
This is a rockstar code 
 The Forum: a club -> (1, 4) -> 114 (ASCII for r)
 The Vision: a a a -> (1, 1, 1) -> 111 (ASCII for o)
 The Event: wonderful spectacle -> (9, 9) -> 99 (ASCII for c)
 Kurukshetra: technology display -> (10, 7) -> 107 (ASCII for k)
 The Workshop: technology drive -> (10, 5) -> 105 (ASCII for i)
 The Code: a university -> (1, 10) -> 110 (ASCII for n)
 The Expo: technology hub -> (10, 3) -> 103 (ASCII for g)
Found the flag: CTF{rocking_in_the_stars}

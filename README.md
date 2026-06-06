cat > README.md << 'EOF'
# Password Audit Lab

## Environment
- OS: Lubuntu (Cisco Cybersecurity LabVM) in VirtualBox
- Tools: Python 3 (hashcat unavailable due to VM memory constraints)
- Wordlist: rockyou.txt (133MB, ~14M real-world passwords)

## Hash Type
- Algorithm: SHA-1
- Source: Self-generated test hashes from known weak passwords

## Methodology
1. Set up isolated VM environment (VirtualBox)
2. Generated SHA-1 hashes of 5 common passwords using sha1sum
3. Downloaded rockyou.txt wordlist (real breach data, 2009)
4. Wrote Python script to replicate dictionary attack logic
5. Script hashes each wordlist entry and compares against targets

## Results
- Hashes attempted: ~14,000,000
- Hashes cracked: 5/5
- Crack rate: 100%
- Time: under 60 seconds on CPU only

## Key Findings
- All 5 passwords appeared in rockyou.txt
- Common passwords (123456, qwerty, letmein) cracked immediately
- SHA-1 is unsalted — identical passwords produce identical hashes
- No GPU required for dictionary attacks against weak passwords

## What I Learned
- How one-way hashing works and why it isn't encryption
- Why dictionary attacks are effective against real-world passwords
- The difference between SHA-1 (weak/fast) and bcrypt/Argon2 (slow/salted)
- Why password reuse across breaches is dangerous
- Safe lab practices using VM isolation

## Tools Used
- VirtualBox — isolated lab environment
- sha1sum — hash generation
- rockyou.txt — industry standard wordlist
- Python 3 hashlib — cracking script
EOF

cat README.md

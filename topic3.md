# Topic 3
The Power of the Command Line

## 3.1
Archiving Files on the Command Line  
Weight: 2 

### Introduction
- Compression
    - Reduces space consumption
    - Reduces data transfer size on networks
- Lossless
    - Can be uncompressed back to original
- Lossy
    - Cannot be recovered
    - Often used when:
        - Quality loss is imperceptible for humans
        - Space is more valuable than quality
        - Quality is irrelevant to context
- Archiving tools
    - Used to bundle files/dirs. into single file
    - Common uses:
        - Backups
        - Bundled source code
        - Data retention 
    - Compression capabilities range from:
        - Optional
        - Default
        - Not included
- `tar`
    - Most common Linux archiver
    - On it's own manages but does not compress
- Linux compression tools
    - Lossless
        - `bzip2`
        - `gzip`
        - `xz`
    - Each tool uses a different algorithm
        - Won't work interchangeably
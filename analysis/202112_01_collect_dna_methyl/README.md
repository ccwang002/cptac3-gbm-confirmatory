## Annotations
It requires the EPIC probe manifest and annotation in hg38 obtained from https://zwdzwd.github.io/InfiniumAnnotation (DOI: 10.1093/nar/gkw967).

    curl --create-dirs -o annotations/EPIC.hg38.manifest.rds -L \
        https://zhouserver.research.chop.edu/InfiniumAnnotation/20180909/EPIC/EPIC.hg38.manifest.rds
    curl --create-dirs -o annotations/EPIC.hg38.manifest.gencode.v22.rds -L \
        https://zhouserver.research.chop.edu/InfiniumAnnotation/20180909/EPIC/EPIC.hg38.manifest.gencode.v22.rds

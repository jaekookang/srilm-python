# srilm-python
Python binding for SRI Language Modeling Toolkit implemented in Cython

Read the docs at: http://srilm-python.readthedocs.org

# NOTE (building on macOS Sierra)
- When building srilm (under kaldi), follow steps below:
  - 1) Unzip srilm under tools/srilm
  - 2) git clone SRILM-PYTHON under tools/srilm
  - 3) Patch MEModel.cc. $SRILM should be full path.
  
    ```bash
    $ cd srilm-python
    $ patch $SRILM/lm/src/MEModel.cc < srilm/MEModel.cc.patch
    ```
    
  - 4) Edit extras/install_srilm.sh
    - Comment out line 30: # tar -xvzf ../srilm.tgz to prevent overwriting
    - Change line 59: `make` --> `make NO_ICONV=1 LDFLAGS='-L/usr/local/lib' World`
      - NO_ICONV: avoid iconv error
      - LDFLAGS: set iconv path (might not necessary if NO_ICONV=1)
      - If srilm is built under kaldi, use $KALDI/tools/extra/install_srilm.sh
      
  - 5) Build srilm
  
    ```bash
    . ./extras/install_srilm.sh
    ```
    
  - 6) Build srilm-python
  
    ```bash
    make NO_ICONV=1 HAVE_LIBLBFGS=1 LDFLAGS='-L/usr/local/lib'
    ```
  
  
  
    
    

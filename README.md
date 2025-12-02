# 國教院中文斷詞系統

## 安裝 Segmentor_py3 之前必需先安裝 CRF++
* 下載處：https://github.com/mhbai/CRFPP.git

## 安裝 Segmentor_py3

* 下載程式碼：

	```$ git clone https://github.com/mhbai/Segmentor_py3.git```
    
* 下載斷詞及詞性標記模型：
	* 進入 Segmentor_py3/Segmentor 目錄下，下載模型並解壓縮

		```
        $ cd Segmentor_py3/Segmentor
        $ gdown https://drive.google.com/uc?id=1P75f9sCNZCarD5s1n2JEM0TQvmwAouPj
		$ tar zxvf naer-segmentor-models-xxx.tar.gz
		```
    * 如果沒有 gdown ，請先安裝
        ```
        $ pip install gdown
        ```

*  安裝程式與資料：
	* 在 Segmentor_py3 目錄下執行安裝：

	    ```
	    $ python setup.py build
	    $ pip install .
	    ```

## Segmentor 模組簡易使用方法

```
>>> import json
>>> from Segmentor import *
>>> segmenter=Segmentor()
>>> words=segmenter.segment(u"中文斷詞系統。")
>>> print json.dumps(words,ensure_ascii=False)
>>> ["中文", "斷詞", "系統", "。"]
```
	    
## 命令列參數說明

```
Usage: naer_seg [options] input_file1[::output_file1] ...

Options:
  -h, --help            show this help message and exit
  -s SUFFIX, --suffix=SUFFIX
                        suffix for output file
  -m MODEL, --model=MODEL
                        directory of models for word segmention and POS
                        tagging
  -p, --postag          POS tagging switch
  -n, --disable-segment
                        segmentation switch
  -b BOUNDARY, --boundary=BOUNDARY
                        word boundary
  -f FORMAT, --format=FORMAT
                        output format for a tagged word
  --output-dir=OUTPUTDIR
                        save output files to specific directory
  -l LIST, --list=LIST  read input file list from file
  -v, --verbose         enable verbose mode
  -e ENCODING, --encoding=ENCODING
                        set input and output encoding
  --region=REGION       set processing region. e.g.
                        --region="<chtitle>::</chtitle>" will segment text
                        between <chtitle> and </chtitle> tags. "::" is the
                        separator of the start and end tags.
  --mask=MASK           set mask region which will not be processed. e.g.
                        --mask="<[^>]+>" will prevent html tags, such as <font
                        size="12">, to be segmented.
  -D DIRECTORY, --directory=DIRECTORY
                        set input (and output) directory. e.g.
                        --directory="dir1::dir2" will process files in dir1
                        and output to dir2.
  --exclude=EXCLUDE     set exclude regular expression.
  --include=INCLUDE     set include regular expression.
```

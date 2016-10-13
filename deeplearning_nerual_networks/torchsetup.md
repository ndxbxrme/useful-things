```
    1  sudo apt-get update
    2  sudo apt-get install gdebi
    3  cd Downloads/
    4  sudo gdebi google-chrome-stable_current_amd64.deb 
    5  ls
    6  mkdir dev
    7  cd dev/
    8  apt search cuda
    9  sudo apt-get install nvidia-cuda-toolkit
   10  curl
   11  curl -s https://raw.githubusercontent.com/torch/ezinstall/master/install-deps | bash
   12  sudo apt-get install libqt4core libqt4gui
   13  sudo apt-get install libqtcore4 libqtgui4
   14  git clone https://github.com/torch/distro.git ~/torch --recursive
   15  sudo apt-get install git
   16  git clone https://github.com/torch/distro.git ~/torch --recursive
   17  sudo apt install cmake
   18  sudo apt-get install -y build-essential gcc g++ curl cmake libreadline-dev git-core libqt4-dev libjpeg-dev libpng-dev ncurses-dev imagemagick libzmq3-dev gfortran unzip gnuplot gnuplot-x11 ipython
   19  cd ~/torch
   20  ./install.sh
   21  source ~/.bashrc
   22  sudo apt-get -y install python2.7-dev
   23  sudo apt-get install libhdf5-dev
   24  cd ..
   25  luarocks install torch
   26  luarocks install nn
   27  luarocks install optim
   28  luarocks install lua-cjson
   29  cd ..
   30  cd a/
   31  cd dev/
   32  git clone https://github.com/deepmind/torch-hdf5
   33  cd torch-hdf5/
   34  luarocks make hdf5-0-0.rockspec 
   35  cd ..
   36  luarocks install cutorch
   37  luarocks install cunn
   38  git clone https://github.com/jsjohnson/torch-rnn
   39  git clone https://github.com/jcjohnson/torch-rnn
   40  cd torch-rnn/
   41  pip install -r requirements.txt 
   42  sudo apt-get install python-pip
   43  pip install -r requirements.txt 
   44  pip install --upgrade pip
   45  python scripts/preprocess.py --input_txt data/bluespiano.txt --output_h5 data/bluespiano.h5 --output-json data/bluespiano.json
   46  python scripts/preprocess.py --input_txt data/bluespiano.txt --output_h5 data/bluespiano.h5 --output_json data/bluespiano.json
   47  ls data/
   48  th train.lua -input_h5 data/bluespiano.h5 -input_json data/bluespiano.json 
   49  ls
   50  cd cv/
   51  ls
   52  cd ..
   53  mkdir finished
   54  cd finished/
   55  mkdir bluespiano
   56  cd bluespiano/
   57  mv ../../cv/*.* .
   58  ls
   59  cd ../../cv
   60  ls
   61  cd ..
   62  cd data/
   63  wget https://github.com/jamesthomson/Evolution_of_Pop_Lyrics/blob/master/data/scraped_lyrics.tsv poplyrics.txt
   64  ls
   65  mv scraped_lyrics.tsv poplyrics.txt
   66  cd ..
   67  python scripts/preprocess.py --input_txt data/poplyrics.txt --output_h5 data/poplyrics.h5 --output_json data/poplyrics.json
   68  th train.lua -input_h5 data/poplyrics.h5 -input_json data/poplyrics.json 
   69  cd data/
   70  rm poplyrics.*
   71  ls
   72  wget https://github.com/jamesthomson/Evolution_of_Pop_Lyrics/blob/master/data/scraped_lyrics.tsv?raw=true
   73  python scripts/preprocess.py --input_txt data/poplyrics.txt --output_h5 data/poplyrics.h5 --output_json data/poplyrics.json
   74  cd ..
   75  python scripts/preprocess.py --input_txt data/poplyrics.txt --output_h5 data/poplyrics.h5 --output_json data/poplyrics.json
   76  cd data/
   77  mv scraped_lyrics.tsv\?raw\=true poplyrics.txt
   78  python scripts/preprocess.py --input_txt data/poplyrics.txt --output_h5 data/poplyrics.h5 --output_json data/poplyrics.json
   79  cd ..
   80  python scripts/preprocess.py --input_txt data/poplyrics.txt --output_h5 data/poplyrics.h5 --output_json data/poplyrics.json
   81  th train.lua -input_h5 data/poplyrics.h5 -input_json data/poplyrics.json 
   82  cd cv/
   83  ls
   84  rm *.*
   85  cd ..
   86  th train.lua -input_h5 data/poplyrics.h5 -input_json data/poplyrics.json 
   87  ls cv/
   88  th sample.lua -checkpoint cv/checkpoint_298000.t7 -length 2000
   89  th sample.lua -checkpoint cv/checkpoint_298000.t7 -length 2000 -seed 23
   90  th sample.lua -checkpoint cv/checkpoint_298000.t7 -length 2000
   91  th sample.lua -checkpoint cv/checkpoint_298000.t7 -length 2000 -temperature 0.01
   92  th sample.lua -checkpoint cv/checkpoint_298000.t7 -length 2000 -sample 1
   93  th sample.lua -checkpoint cv/checkpoint_298000.t7 -length 2000 -temperature 2
   94  th sample.lua -checkpoint cv/checkpoint_298000.t7 -length 2000 -temperature 0.9
   95  history | grep Wrong
   96  history | grep echo
   97  cd dev/
   98  cd torch-rnn/
   99  ls
  100  cd data/
  101  ls
  102  echo hey > okskype.txt
  103  gedit okskype.txt 
  104  cd ..
  105  gedit lyrics.txt 
  106  cd dev/torch-rnn/
  107  ls
  108  th sample.lua -checkpoint cv/checkpoint_2000.t7
  109  th sample.lua -checkpoint cv/checkpoint_3000.t7
  110  th sample.lua -checkpoint cv/checkpoint_5000.t7
  111  th sample.lua -checkpoint cv/checkpoint_5000.t7 -temperature 0.7
  112  th sample.lua -checkpoint cv/checkpoint_13000.t7 -temperature 0.7
  113  th sample.lua -checkpoint cv/checkpoint_13000.t7 -temperature 1
  114  th sample.lua -checkpoint cd dev/
  115  cd torch-rnn/
  116  python scripts/preprocess.py --input_txt data/okskype.txt --output_h5 okskype.h5 --output_json okskype.json
  117  th train.lua -input_h5 okskype.h5 -input_json okskype.json
  118  ls cv/checkpoint_
  119  ls cv/
  120  python scripts/preprocess.py --input_txt data/okskype.txt --output_h5 okskype.h5 --output_json okskype.json
  121  th train.lua -input_h5 okskype.h5 -input_json okskype.json
  122  cd dev/torch-rnn/
  123  th sample.lua -checkpoint cv/checkpoint_2000.t7
  124  th sample.lua -checkpoint cv/checkpoint_6000.t7
  125  th sample.lua -checkpoint cv/checkpoint_6000.t7 -temperature 0.7
  126  th sample.lua -checkpoint cv/checkpoint_6000.t7 -temperature 0.2
  127  th sample.lua -checkpoint cv/checkpoint_6000.t7 -temperature 0.5
  128  th sample.lua -checkpoint cv/checkpoint_6000.t7 -temperature 0.8 -length 100000 > chat.txt
  129  cd dev/torch-rnn/
  130  history | grep th
  131  ls /media/a
  132  mkdir /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/okskype
  133  mv /cv/*.* /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/okskype/
  134  mv cv/*.* /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/okskype/
  135  ls cv/
  136  python scripts/preprocess.py --input_txt data/poplyrics.txt --output_h5 data/poplyrics.h5 --output_json data/poplyrics.json
  137  cd dev/torch-rnn/
  138  history | grep python
  139  python scripts/preprocess.py --input_txt /media/a/D0BCE68FBCE67000/DEV/temp/skype-history/okchat.txt --output_h5 data/okchat.h5 --output_json data/okchat.json
  140  history | grep th
  141  th train.lua -input_h5 data/okchat.h5 -input_json data/okchat.json
  142  th sample.lua -checkpoint cv/checkpoint_50500.t7 
  143  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.9
  144  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.8
  145  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.7
  146  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.6
  147  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.5
  148  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.2
  149  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.1
  150  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.123
  151  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 1.1
  152  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.777
  153  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.1 -length 20000
  154  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 1 -length 20000
  155  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.777 -length 20000
  156  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 1 -length 20000
  157  Oli Knight: asscafe
  158  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 1 -length 2000 -sample 1
  159  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 1 -length 2000 -sample 0
  160  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 1 -length 2000 -sample 0.1
  161  mkdir /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/okchat
  162  mv cv/*.* /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/okchat/
  163  th train.lua -input_h5 data/okchat.h5 -input_json data/okchat.json -model_type rnn -num_layers 3 -rnn_size 512
  164  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 1 -length 2000 -sample 0.1
  165  th sample.lua -checkpoint cv/checkpoint_50500.t7
  166  python3
  167  pip3
  168  sudo apt install python3-pip
  169  pip3 install google_speech
  170  sudo apt install sox libsox-fmt-mp3
  171  google_speech -l en stall -e delay 0.5 overdrive 20 repeat 5 speed 0.9 gain -5
  172  google_speech -h
  173  google_speech -l en stall -e delay 0.5 overdrive 20 repeat 5 speed 0.9 gain -5 -v debug
  174  sox -h
  175  gedit
  176  cd dev/torch-rnn/
  177  th sample.lua cv/checkpoint_52000.t7 
  178  th sample.lua -checkpoint cv/checkpoint_52000.t7 
  179  th sample.lua -checkpoint cv/checkpoint_52000.t7 -temperature 0.7
  180  th sample.lua -checkpoint cv/checkpoint_52000.t7 -temperature 0.7 -start_text A
  181  th sample.lua -checkpoint cv/checkpoint_52000.t7 -start_text A
  182  th sample.lua -checkpoint cv/checkpoint_61000.t7 -start_text A
  183  th sample.lua -checkpoint cv/checkpoint_134000.t7 -start_text A
  184  th sample.lua -checkpoint cv/checkpoint_134000.t7 -start_text A -temperature 0.1
  185  th sample.lua -checkpoint cv/checkpoint_134000.t7 -start_text A -temperature 0.2
  186  th sample.lua -checkpoint cv/checkpoint_134000.t7 -start_text A -temperature 0.3
  187  th sample.lua -checkpoint cv/checkpoint_134000.t7 -start_text A -temperature 0.4
  188  th sample.lua -checkpoint cv/checkpoint_134000.t7 -start_text A -temperature 0.5
  189  th sample.lua -checkpoint cv/checkpoint_168000.t7 -start_text A -temperature 1
  190  th sample.lua -checkpoint cv/checkpoint_168000.t7 -start_text A -temperature 0.8
  191  th sample.lua -checkpoint cv/checkpoint_168000.t7 -start_text A -temperature 0.9
  192  cd dev/
  193  cd torch-rnn/
  194  ls
  195  ls cv/
  196  th sample.lua -checkpoint cv/checkpoint_50500.t7
  197  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.8
  198  th sample.lua -checkpoint cv/checkpoint_50500.t7 -temperature 0.9
  199  mkdir /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/okchat_rnn_3_512
  200  mv cv/* /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/okchat_rnn_3_512/
  201  history | grep train.lua
  202  th train.lua -input_h5 data/poplyrics.h5 -input_json data/poplyrics.json -model_type rnn -num_layers 3 -rnn_size 512
  203  cd dev/torch-rnn/
  204  ls
  205  ls cv/
  206  cd cv/
  207  rm *
  208  ls
  209  cd ..
  210  history | grep python
  211  python scripts/preprocess.py --input_txt /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/blues2txt/build/input.txt --output_h5 data/blues.h5 --output_json data/blues.json
  212  history | grep train
  213  th train.lua -input_h5 data/blues.h5 -input_json data/blues.json -num_layers 3 -rnn_size 512
  214  th train.lua -input_h5 data/blues.h5 -input_json data/blues.json
  215  wc -m < /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/blues2txt/build/input.txt 
  216  th sample.lua -checkpoint cv/checkpoint_174900.t7
  217  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm:
  218  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 1000000 | /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output10.txt
  219  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 1000000 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output10.txt
  220  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output10.txt
  221  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.9 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output10.txt
  222  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 1 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output10.txt
  223  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.9 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output09.txt
  224  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.8 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output08.txt
  225  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.7 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output07.txt
  226  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.6 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output06.txt
  227  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.5 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output05.txt
  228  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.4 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output04.txt
  229  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.3 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output03.txt
  230  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.2 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output02.txt
  231  th sample.lua -checkpoint cv/checkpoint_174900.t7 -start_text bpm: -length 100000 -temperature 0.1 > /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/build/output01.txt
  232  cd dev/torch-rnn/
  233  history | grep sample
  234  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7
  235  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7 -length 10000 | clip
  236  xclip
  237  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7 -length 10000
  238  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7 -length 10000 -temperature 0.7
  239  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7 -length 10000 -temperature 0.2
  240  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7 -length 10000 -temperature 0.2 > bluex.txt
  241  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7 -length 100000 -temperature 0.2 > bluex.txt
  242  gedit bluex.txt 
  243  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7 -length 100000 -temperature 0.1 > bluex01.txt
  244  gedit bluex01.txt 
  245  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7 -length 100000 -temperature 0.3 > bluex03.txt
  246  gedit bluex03.txt 
  247  th sample.lua -checkpoint cv/checkpoint_232000.t7
  248  th sample.lua -checkpoint cv/checkpoint_232000.t7 -temperature 0.1
  249  th sample.lua -checkpoint cv/checkpoint_232000.t7 -temperature 0.3
  250  th sample.lua -checkpoint cv/checkpoint_232000.t7 -temperature 0.5
  251  th sample.lua -checkpoint cv/checkpoint_232000.t7 -temperature 0.7
  252  th sample.lua -checkpoint cv/checkpoint_239000.t7 -temperature 0.7
  253  th sample.lua -checkpoint cv/checkpoint_239000.t7 -temperature 1
  254  th sample.lua -checkpoint cv/checkpoint_262000.t7 -temperature 1
  255  I know that you were made to let me down
  256  th sample.lua -checkpoint cv/checkpoint_262000.t7 -temperature 1
  257  th sample.lua -checkpoint cv/checkpoint_262000.t7 -temperature 0.1
  258  th sample.lua -checkpoint cv/checkpoint_265000.t7 -temperature 1
  259  cd dev/torch-rnn/
  260  th sample -checkpoint cv/checkpoint_78000.t7
  261  th sample.lua -checkpoint cv/checkpoint_78000.t7
  262  th sample.lua -checkpoint cv/checkpoint_81000.t7
  263  th sample.lua -checkpoint cv/checkpoint_81000.t7 -temperature 0.1
  264  th sample.lua -checkpoint cv/checkpoint_81000.t7 -temperature 0.2
  265  th sample.lua -checkpoint cv/checkpoint_81000.t7 -temperature 0.3
  266  th sample.lua -checkpoint cv/checkpoint_81000.t7 -temperature 0.4
  267  th sample.lua -checkpoint cv/checkpoint_81000.t7 -temperature 0.5
  268  th sample.lua -checkpoint cv/checkpoint_81000.t7 -temperature 0.6
  269  th sample.lua -checkpoint cv/checkpoint_81000.t7 -temperature 0.7
  270  th sample.lua -checkpoint cv/checkpoint_81000.t7 -temperature 0.8
  271  th sample.lua -checkpoint cv/checkpoint_96000.t7 -temperature 0.8
  272  th sample.lua -checkpoint cv/checkpoint_96000.t7 -temperature 0.9
  273  th sample.lua -checkpoint cv/checkpoint_119000.t7 -temperature 0.9
  274  th sample.lua -checkpoint cv/checkpoint_124000.t7 -temperature 0.9
  275  th sample.lua -checkpoint cv/checkpoint_124000.t7 -temperature 1.1
  276  th sample.lua -checkpoint cv/checkpoint_124000.t7 -temperature 1
  277  th sample.lua -checkpoint cv/checkpoint_155000.t7 -temperature 1
  278  th sample.lua -checkpoint cv/checkpoint_155000.t7 -temperature 1.5
  279  th sample.lua -checkpoint cv/checkpoint_155000.t7 -temperature 1.4
  280  th sample.lua -checkpoint cv/checkpoint_155000.t7 -temperature 1.3
  281  th sample.lua -checkpoint cv/checkpoint_155000.t7 -temperature 1.2
  282  th sample.lua -checkpoint cv/checkpoint_155000.t7 -temperature 1.1
  283  th sample.lua -checkpoint cv/checkpoint_161000.t7
  284  th sample.lua -checkpoint cv/checkpoint_176000.t7
  285  cd ..
  286  cd /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/
  287  grunt
  288  cd ~/dev/
  289  cd torch-rnn/
  290  ls
  291  th sample.lua -checkpoint cv/checkpoint_201000.t7
  292  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_
  293  th sample.lua -checkpoint /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/checkpoint_174900.t7
  294  cd /media/a/D0BCE68FBCE67000/DEV/temp/notestream-player/
  295  grunt
  296  cd dev/torch-rnn/
  297  mkdir /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter
  298  mv cv/* /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter/
  299  history | grep train
  300  th train.lua -input_h5 data/blues.h5 -input_json data/blues.json -num_layers 3 -rnn_size 512
  301  mkdir /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2
  302  mv cv/* /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/bluesbetter2/
  303  th train.lua -input_h5 data/poplyrics.h5 -input_json data/poplyrics.json -num_layers 3 -rnn_size 512
  304  cd dev/torch-rnn/
  305  th sample.lua -checkpoint cv/checkpoint_298000.t7
  306  th sample.lua -checkpoint cv/checkpoint_298000.t7 -temperature 0.9
  307  th sample.lua -checkpoint cv/checkpoint_298000.t7 -temperature 0.1
  308  th sample.lua -checkpoint cv/checkpoint_298000.t7 -temperature 0.2
  309  th sample.lua -checkpoint cv/checkpoint_298000.t7 -temperature 0.3
  310  th sample.lua -checkpoint cv/checkpoint_298000.t7 -temperature 1
  311  cd dev/torch-rnn/
  312  th sample.lua -checkpoint cv/checkpoint_298000.t7 -temperature 1
  313  cd /media/a/D0BCE68FBCE67000/
  314  cd DEV/andy/
  315  git clone https://github.com/MakeITSimpleUK/hip
  316  cd dev/torch-rnn/
  317  mkdir /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/poplyrics_3_512
  318  mv cv/* /media/a/D0BCE68FBCE67000/DEV/temp/deeplearning/finished/poplyrics_3_512/
  319  history | grep "python"
  320  python scripts/preprocess.py --input_txt /media/a/D0BCE68FBCE67000/DEV/temp/skype-history/akchat.txt --output_h5 data/akchat.h5 --output_json data/akchat.json
  321  history | grep sample.lua
  322  history | grep train.lua
  323  th train.lua -input_h5 data/akchat.h5 -input_json data/akchat.json -num_layers 3 -rnn_size 512
  324  th sample.lua -checkpoint cv/checkpoint_5350.t7
  325  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.8
  326  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.1
  327  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.3
  328  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.5
  329  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.7
  330  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.6
  331  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 1
  332  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 1 -length 50
  333  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 1 -length 50 -start_text "Kieron Wright: ok"
  334  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 1 -length 50 -start_text "Kieron Wright: ok\n"
  335  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 1 -length 50 -start_text "Kieron Wright: ok"
  336  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 1 -length 100 -start_text "Kieron Wright: ok"
  337  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.1 -length 100 -start_text "Kieron Wright: ok"
  338  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.1 -length 100 -start_text "Kieron Wright: hey"
  339  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.3 -length 100 -start_text "Kieron Wright: hey"
  340  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.6 -length 100 -start_text "Kieron Wright: hey"
  341  th train.lua -input_h5 data/akchat.h5 -input_json data/akchat.json -num_layers 4 -rnn_size 512
  342  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 1
  343  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.6
  344  th train.lua -input_h5 data/akchat.h5 -input_json data/akchat.json
  345  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 1
  346  history | grep train
  347  th train.lua -input_h5 data/akchat.h5 -input_json data/akchat.json -model-type rnn -num_layers 3 -rnn_size 512
  348  th train.lua -input_h5 data/akchat.h5 -input_json data/akchat.json -model_type rnn -num_layers 3 -rnn_size 512
  349  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 1
  350  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.8
  351  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.1
  352  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.3
  353  th sample.lua -checkpoint cv/checkpoint_5350.t7 -temperature 0.6
  354  history
  355  cd dev/
  356  history > history.txt
```

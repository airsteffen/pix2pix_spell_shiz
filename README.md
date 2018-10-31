# pix2pix_spell_shiz  
Copy from gaelhugo's pix2pix-tensorflow-spell


#### Upload traing data on spell ressources
`$ spell upload sticks`

#### Training pix2pix with the data
**--ngf 64 and --ndf 64 might be needed**  

1. Try `--max_epochs 50`  
`$ spell run --machine-type V100 --framework tensorflow "python pix2pix.py --mode train --input_dir Iris --output_dir ckpt --which_direction AtoB --max_epochs 50 --ngf 64 --ndf 64" -m uploads/Iris`

2. Try `--max_epochs 200`
`$ spell run --machine-type V100 --framework tensorflow "python pix2pix.py --mode train --input_dir Iris --output_dir ckpt --which_direction AtoB --max_epochs 200 --ngf 64 --ndf 64" -m uploads/Iris`




#### Export the model
`$ spell run --machine-type V100 --framework tensorflow "python pix2pix.py --mode export --output_dir export/ --checkpoint ckpt --which_direction AtoB" -m runs/RUN_ID/ckpt`

 
#### Download the model
`$ spell cp runs/RUN_ID/export`


#### Convert model to tensorflow.js/ml5js bin
'''with python3.7'''

#### Convert the optimized model to tensorflow.js
`$ python export-checkpoint.py --checkpoint ./export --output_file static/models/yourModelName.pict`


#### *if issue with tensorflow:*   
`$ pip install --upgrade https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-0.12.0-py3-none-any.whl`

----
`$ python export-checkpoint.py --checkpoint ckpt --output_file model_AtoB.bin`
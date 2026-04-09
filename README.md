# effectorp_fungal_usage_pipeline
# mamba install predector::effectorp3
# opt_path='/Users/liangdong/miniconda3/bin'
# name='C_siamense_JDA_12'
python3 $opt_path/EffectorP3.py \
    -f \
    -i ${name}.fa \
    -o ${name}.Effectors.out.txt \
    -E ${name}.Effectors.out.fasta

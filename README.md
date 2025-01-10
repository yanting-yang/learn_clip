# Learn CLIP

Build image

```bash
docker build -t ghcr.io/yanting-yang/learn_clip:250109 .
```

Test image

```bash
docker run -it --rm --gpus=all --ipc=host ghcr.io/yanting-yang/learn_clip:250109
```

Push image

```bash
docker push ghcr.io/yanting-yang/learn_clip:250109
```

Run `03_run_clip.py`

```bash
python 03_run_clip.py \
    --output_dir ./clip-roberta-finetuned \
    --model_name_or_path ./clip-roberta \
    --trust_remote_code \
    --data_dir ./dummy_data/ \
    --dataset_name ydshieh/coco_dataset_script \
    --dataset_config_name=2017 \
    --image_column image_path \
    --caption_column caption \
    --remove_unused_columns=False \
    --do_train  --do_eval \
    --per_device_train_batch_size="64" \
    --per_device_eval_batch_size="64" \
    --learning_rate="5e-5" --warmup_steps="0" --weight_decay 0.1 \
    --overwrite_output_dir \
    --push_to_hub
```

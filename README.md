# LibriTTS-P: A Corpus with Speaking Style and Speaker Identity Prompts for Text-to-Speech and Style Captioning
We introduce LibriTTS-P, a new corpus based on LibriTTS-R that includes utterance-level descriptions (i.e., prompts) of speaking style and speaker-level prompts of speaker characteristics. We employ a hybrid approach to construct prompt annotations: (1) manual annotations that capture human perceptions of speaker characteristics and (2) synthetic annotations on speaking style. Compared to existing English prompt datasets, our corpus provides more diverse prompt annotations for all speakers of LibriTTS-R. Experimental results for prompt-based controllable TTS demonstrate that the TTS model trained with LibriTTS-P achieves higher naturalness than the model using the conventional dataset. Furthermore, the results for style captioning tasks show that the model utilizing LibriTTS-P generates 2.5 times more accurate words than the model using a conventional dataset.

You can check the [paper]() and [demo page]().
## File Details
There are files related to LibriTTS-P under the `data` directory.
The details of each file are as follows:
- `df1_en.csv`, `df2_en.csv`, `df3_en.csv`
  - Speaker prompt data for Annotator 1, Annotator 2, and Annotator 3, respectively.
- `excluded_spk_list.txt`
  - We found that in LibriTTS-R, there are voice samples with the same spk_id that clearly have different genders. This is a text file listing those spk_ids. We recommend excluding these when using our dataset.
- `unannotated_spk_list.txt`
  - Audio files listed in "libritts_r_failed_speech_restoration_examples.tar.gz" (see [LibriTTS-R cite](https://www.openslr.org/141/)) were excluded during the annotation for speaker prompts. As a result, there were no suitable audio files left for annotation for three speakers. Therefore, we have documented these spk_ids in this text file. We recommend excluding these speakers when using speaker prompts.
- `style_prompt_candidates_v230922.csv`
  - This file includes the style_prompt_key (e.g., M_p-low_s-slow_e-low) and the corresponding style prompt options, separated by semicolons.
  - The style_prompt_key comprises four style factors:
    - Gender: M/F
    - Pitch: low/normal/high
    - Speaking speed: slow/normal/fast
    - Loudness: low/normal/high
  - For example, "M_p-low_s-slow_e-low" means the following:
    ```
    M: male
    p-low: pitch is low
    s-slow: speaking speed is slow
    e-low: loudness is low
    ```
- `metadata_w_style_prompt_tags_v230922.csv`
  - This file contains metadata for each audio file. For instance, by using this file along with style_prompt_candidates_v230922.csv, it is possible to refer to the style_prompt for each audio.
  - The details of the columns in this CSV file are as follows:
    | Name               | Description                                                    |
    |--------------------|----------------------------------------------------------------|
    | item_name          | Name of the audio file                                        |
    | spk_id             | Speaker ID                                    |
    | gender             | Gender of the speaker                                         |
    | pitch              | Pitch level of the audio                                      |
    | speaking_speed     | Speaking speed level |
    | energy             | Energy level of the audio|
    | content_prompt     | Content prompt corresponding to the audio|
    | style_prompt_key   | Key for `style_prompt_candidates_v230922.csv`, indicating the style prompt associated with the audio. |
    | raw_f0_mean        | Average F0 of the voiced parts of the audio |
    | raw_f0_scale       | Standard deviation of the F0 |
    | raw_lf0_mean       | Average of the log-F0 for the voiced parts |
    | raw_lf0_scale      | Standard deviation of the logarithm of the log-F0|
    | raw_speaking_rate  | The number of syllables per second |
    | raw_loudness_lufs  | Loudness units relative to full scale |
    | raw_loudness_mean  | Average loudness of the audio file calculated per frame, providing an average measure of the loudness over time. |
    | raw_loudness_scale | Standard deviation of the frame loudness values, indicating the variability of loudness across the audio frames. |
    | invalid            | Flag indicating whether the utterance has been marked as invalid due to missing F0, an invalid speaking rate (e.g., speaking_rate < 0), or other processing errors. `1` means invalid, and `0` means valid. |
(For detailed calculation methods of each item, please refer to [LibriTTS-P paper]().)

You can use audio from [LibriTTS-R](https://www.openslr.org/141/).

## Citation
```
@inproceedings{libritts-p,
    authors={anonymous},
    title={LibriTTS-P: A Corpus with Speaking Style and Speaker Identity Prompts for Text-to-Speech and Style Captioning},
    booktitle={Proc. Under Submission},
    month=sep,
    year=2024
}
```
## License
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

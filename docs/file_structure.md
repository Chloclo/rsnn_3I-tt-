project_root/
├── README.md
├── requirements.txt
├── analysis/
│   ├── scripts/                # scripts to analyze data and create plots
│   ├── plots/                  # plots saved
│   └── intermediary/           # any intermediary files or images 
├── data/
│   ├── input/           
|   |   ├── training_data...csv files   # raw training data
|   |   ├── spike_gen.ipynb             # file to generate raw training data
|   |   └── Sine_Wave_Dataset/         # functions that process the raw input data for training models
│   ├── output/                        # output (all saved data including model weights, losses, spike rasters... in terabytes)
├── models/
│   ├── rsnn/                   # all RSNN models reside here
│   |── Custom_Loss/            # custom loss classes (only task_loss is used; loss classes with synchrony, firing rate and criticality │   |                               haven't been used.)
│   └── train1.py               # the training function
├── scripts/                    # Scripts that are run! (combinations of task and model variations)
├── utils/
│   ├── rleaky_refractory_period.py     # the LIF model that integrates refractory period (imported in 
│   |                                   # models)
│   └── helper1.py              # file that houses most helper functions!
├── docs/
    ├── file_structure.md
    ├── data_structure.md
    ├── analysis_guidelines.md
    └── future_work.md
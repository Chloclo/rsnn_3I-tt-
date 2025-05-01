task{taskid}_i{ineuron}_job{job}_epoch{epoch}_batch{i}.pth

taskid: "AP", "A", "P", "SC"
    AP: changing amplitude and changing period
    A: only changing amplitude, constant period
    P: only changing period, constant amplitude
    SC: synchronization continuation (amplitude and period both provided for the first 10s)
    
    all 4 task types include 3 inputs to the model: amplitude vector, period vector, and clock input. 
    each model is trained on 1000 samples. for each sample, the amplitude and period vectors are pytorch tensor of constant values. (i.e. [3,3,3,3,3,...]). The clock input is a vector with increasing and resetting time input. (i.e. [0,1,2,3,4,0,1,2,3,4,0...])
    for "changing", the attribute changes across 1000 samples. For "constant", the attribute is constant across all 1000 samples. 

ineuron: "P", "S", "3", "PS"
    P: all 40 inhibitory neurons are PV neurons
    S: all 40 inhibitory neurons are SST neurons
    PS: 24 inhibitory neurons are PV, 16 are SST
    3: 14 PV, 13 SST, 13 5HT

job: 
    each task-ineuron combination (16 in total) is run for 10 jobs with different initial neuron connectivities (using the same distribution). For each job, torch.manual_seed(job) for replicability. 
    in analysis, we calculate statistical significance between distinct task-ineuron combinations by comparing between 10-job observations.

epoch: 
    each job is ran for 1000 epochs. 
    only each 10th epoch is saved: range(0,10,1000). Last saved epoch=990
    In most cases, to get data from the best prediction, use the 990th epoch.

batch: 
    data is divided into 40 distinct batches of 25 samples. DataLoader object manages this(in scripts)
    for most data saves, a result is saved for a unique batch (for all 25 samples):
    (i.e. spikes.shape=[25,200,300], so a 200(#neurons)x300(#timesteps) matrix represents networks' spike behavior to predict for one sample. Network predicts 25 samples before updating it's weights, and we save data once per update. so the first axis value 25 indicates spikes for 25 distinct samples in a batch.)
    
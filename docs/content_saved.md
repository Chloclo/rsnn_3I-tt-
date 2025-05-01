What is in Saved Files?

torch.save({

    "task_loss":criterion.task_loss.item(), (float)
    "spikes":spikes, (tensor: 25x200x300)
    "input_weights":model.l1.weight.data, (tensor: 25x3x200)
    "rec_weights":model.rlif1.recurrent.weight.data, (tensor: 25x200x200)
    "output_weights":model.l2.weight.data, (tensor: 25x200x1)
    "inputs":inputs, 
    "outputs":outputs,
    "targets":targets},

    f'data/output/task{taskid}_i{ineuron}_job{job}_epoch{epoch}_batch{i}.pth')

** the dimensions mentioned might be slightly off (i.e. instead of 25x3x300, input_weights might be 25x300x3)
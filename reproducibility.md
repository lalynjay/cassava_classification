# Instructions for reproducing this project

1. Ensure you have installed all the libraries in the requirements.txt file
2. Obtain zipped data file- it can be downloaded from https://www.kaggle.com/c/cassava-disease/overview
3. The zipped data file will need to be unzipped. This is done by running the following code:

        from zipfile import ZipFile
        with ZipFile("data/cassava-disease.zip", 'r') as zObject:
            zObject.extractall(path='./data')
        
To unzip the data/train file:       
        
    with ZipFile("data/train.zip", 'r') as zObject:
        zObject.extractall(path='./data')
       
       
Running the following:
        
        print(os.listdir("./data/train"))
        print(np.shape(os.listdir("./data/train"))) 

should output:

        \['cbb', 'cbsd', 'cgm', 'cmd', 'healthy']
        (5,)


From here, go into the "data" folder and create a new folder named "short". In the "short" folder, create 5 new subfolders- 
'cbb', 'cbsd', 'cgm', 'cmd', 'healthy'. From here, select the first 300 images in each subfolder from the "data/train" folder, and copy and paste into the respective "data/short" subfolder. 

Running the following lines:

    for sub in os.listdir("./data/short"):
        print(os.listdir("./data/short/" + sub)[:5])
        print(np.shape(os.listdir("./data/short/" + sub)))
        
        
Should output:


    \['train-cbb-0.jpg', 'train-cbb-1.jpg', 'train-cbb-10.jpg', 'train-cbb-100.jpg', 'train-cbb-101.jpg']
    (300,)
    \['train-cbsd-0.jpg', 'train-cbsd-1.jpg', 'train-cbsd-10.jpg', 'train-cbsd-100.jpg', 'train-cbsd-101.jpg']
    (300,)
    \['train-cgm-0.jpg', 'train-cgm-1.jpg', 'train-cgm-10.jpg', 'train-cgm-100.jpg', 'train-cgm-101.jpg']
    (300,)
    \['train-cmd-0.jpg', 'train-cmd-1.jpg', 'train-cmd-10.jpg', 'train-cmd-100.jpg', 'train-cmd-101.jpg']
    (300,)
    \['train-healthy-0.jpg', 'train-healthy-1.jpg', 'train-healthy-10.jpg', 'train-healthy-100.jpg', 'train-healthy-101.jpg']
    (300,)


From here, you should have the data in a format to proceed with running the cells in the notebooks.
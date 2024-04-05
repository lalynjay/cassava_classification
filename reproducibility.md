# Instructions for reproducing this project

1. Ensure you have installed all the libraries in the requirements.txt file
2. Obtain zipped data file- it can be downloaded from https://www.kaggle.com/c/cassava-disease/overview
3. Prepare the data file. The zipped data file will need to be unzipped. This is done by running the following code:

        from zipfile import ZipFile
        with ZipFile("cassava-disease.zip", 'r') as zObject:
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


From here, make the directory for the new image folders:

    ! mkdir "data/short"
    
    
And then the directories for each subfolder:

    ! mkdir "data/short1/cbb"
    ! mkdir "data/short1/cbsd"
    ! mkdir "data/short1/cgm"
    ! mkdir "data/short1/cmd"
    ! mkdir "data/short1/healthy"

To add the first 300 images from each category in the train folder into the respective subfolder, the following code will need to be run:

    # Function to extract all the numbers from the given string
    def getNumbers(str):
    array = re.findall(r'[0-9]+', str)
    num = int(array[0])
    return num
 
    # to add images to the proper directories

    # cbb images
    for filename in os.listdir("data/train/cbb"):
    str = filename
    num = getNumbers(str)
    if num < 300:
        shutil.copy("data/train/cbb/" + filename, "data/short/cbb/" + filename)
        
        
    # cbsd images
    for filename in os.listdir("data/train/cbsd"):
    str = filename
    num = getNumbers(str)
    if num < 300:
        shutil.copy("data/train/cbsd/" + filename, "data/short/cbsd/" + filename)
        
    # cgm images
    for filename in os.listdir("data/train/cgm"):
    str = filename
    num = getNumbers(str)
    if num < 300:
        shutil.copy("data/train/cgm/" + filename, "data/short/cgm/" + filename)
        
    # cmd images
    for filename in os.listdir("data/train/cmd"):
    str = filename
    num = getNumbers(str)
    if num < 300:
        shutil.copy("data/train/cmd/" + filename, "data/short/cmd/" + filename)
        
        
    # healthy images
    for filename in os.listdir("data/train/healthy"):
    str = filename
    num = getNumbers(str)
    if num < 300:
        shutil.copy("data/train/healthy/" + filename, "data/short/healthy/" + filename)
    

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


This code is also present in the final notebook for, but is demonstrated here for ease of reproducibility. From here, you should have the data in a format to proceed with running the cells in the notebooks.
# Project Poster

### Overview 


#### 1) What problem is the student solving?

I analyze the global mortality data to identify the top 5 causes of death based on the average number of deaths between 1990 and 2019. The goal is to visualize the information in a clear and accessible way using a bar graph, helping to highlight which health issues have had the greatest global impact.

#### 2) Where is the information from?

The data comes from a provided CSV file containing cause-of-death statistics by Country/Territory Name and Code, Year, and Causes of Death. Each entry includes a specific cause (e.g., meningitis, diabetes), the year and the number of deaths reported.

    
+ **Country/Territory Name and Code**: The dataset contains records from 204 countries or territories, each identified by both name and a country code.
    

+ **Year**: The year the mortality data was recorded, ranging from 1990 to 2019. This data is reported by researchers at the Institute of Health Metrics and Evaluation (IHME) and the Disease Burden Unit at the World Health Organization (WHO).

<font color="blue">
    
+ **Causes of Death**: The dataset includes the number of deaths for 29 different causes, covering all age groups worldwide. Examples of causes include Meningitis, Cardiovascular Diseases, Malaria, and Alzheimer's Disease.
    
</font>

#### 3) Why is it interesting to the student?

My major is psychology and I'm taking a course related to psychological and neuroscientific diseases, I wondered how large or less those disease's mortality is.

### Design Choices

#### 1) What design choices did the student have to make?

I used top-down design to think about how to code in this project.

- **Data Aggregation** : I chose to compute the average deaths per cause.

- **Filtering** : I selected the top 5 causes with the highest averages to make the chart focused and impactful.

- **Visualization** : I used a bar chart with labelled axes and cleaned x-axis labels for clarity

- **Systematic Program Design** : I used function composition (e.g., find_average → top_5_average → plot_bar_chart) and designed reusable helpers like extract_averages() and generate_x_labels().
means =  top_5_average(find_average(cdl))
    
average_values = extract_averages(means)
#### 2) Why did the student make the choices that she/he made?

I followed the systematic program design approach taught in the course — starting from small functions, testing as I went, and composing them into a final solution. I chose a bar chart because it’s simple, clear, and makes comparisons easy for viewers. Cleaning up axis labels (removing CauseType.) was a small but important detail to enhance readability.

### Problem Solving

To solve the problem, I first wrote functions to calculate the average number of deaths per cause, then identified the top five with the highest averages. Finally, I plotted these using a bar chart.

1. **Read** the mortality dataset from a CSV file.

2. **Compute** average deaths for each cause using find_average().

3. **Sort and Select** the top 5 causes using top_5_average().

4. **Visualize** the results with plot_bar_chart().

![download.png](attachment:5852e287-9c25-492f-b74a-0c4f00a7dfca.png)

### Most challenging

The most difficult part of the project was debugging the top_5_average function. I initially forgot that I wanted to sort a list of tuples before slicing the top 5. I also encountered a ValueError when unpacking, which I solved by making sure each item in the list was a proper (cause, average) tuple.
@typecheck
def top_5_average(avg: List[tuple]) -> List[tuple]:
    """
    Make a list of the top 5 average numbers of mortality per cause.
    The order will be from the most to the least.
    """
#   return [] # stub
    # template based on List[tuple]
    
    n = len(avg
    
    
    for i in range(n):
        for j in range(0, n-i-1):
            cause1, avg1 = avg[j]
            cause2, avg2 = avg[j+1]
            
            if avg1 < avg2:
                avg[j], avg[j+1] = avg[j+1],  avg[j]

    return avg[:5]
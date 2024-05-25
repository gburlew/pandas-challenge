# pandas-challenge

I'd had trouble with creating a path to the csv files that we were supposed to use to make our analysis, so I asked xpert what was wrong with it. Originally, I'd had Path("C:\Users\genna\Desktop\pandas-challenge\Starter_Code\PyCitySchools\Resources\schools_complete.csv"). Apparently, there were issues with how the backslashes were being interpreted, so xpert suggested that I put "r" in front of the rest of my path, so that my path would be interpreted as a raw string. After that, i was able to get the paths to work.

schools = school_data_merge["school_name"].unique()
school_count = schools.count()
xpert suggested nunique function, so the formula ended up being:
school_count = school_data_merge["school_name"].nunique()
school_count

I used the starter code for the passing math score in the example module for how we are supposed to format our analysis. This is the code that I copied: 
passing_math_count = school_data_merge[(school_data_merge["math_score"] >= 70)].count()["student_name"]
passing_math_percentage = passing_math_count / float(student_count) * 100
passing_math_percentage

I ended up using the code above to also calculate the passing reading score and percentage, making changes when necessary. Along with that, here is the rest of the starter code that I ended up using for this project:
passing_math_reading_count = school_data_complete[
    (school_data_complete["math_score"] >= 70) & (school_data_complete["reading_score"] >= 70)
].count()["student_name"]
overall_passing_rate = passing_math_reading_count /  float(student_count) * 100
overall_passing_rate
school_types = school_data.set_index(["school_name"])["type"]
students_passing_math_and_reading = school_data_merge[
    (school_data_merge["reading_score"] >= 70) & (school_data_merge["math_score"] >= 70)
    ninth_graders = school_data_merge[(school_data_merge["grade"] == "9th")]
tenth_graders = school_data_merge[(school_data_merge["grade"] == "10th")]
eleventh_graders = school_data_merge[(school_data_merge["grade"] == "11th")]
twelfth_graders = school_data_merge[(school_data_merge["grade"] == "12th")]
math_scores_by_grade.index.name = None
]
school_students_passing_math_and_reading = students_passing_math_and_reading.groupby(["school_name"]).size()
spending_bins = [0, 585, 630, 645, 680]
labels = ["<$585", "$585-630", "$630-645", "$645-680"]
school_spending_df = per_school_summary.copy()
school_spending_df["Spending Ranges (Per Student)"] =
school_spending_df
spending_math_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"])["Average Math Score"].mean()
spending_reading_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"])["Average Reading Score"].mean()
spending_passing_math = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Passing Math"].mean()
spending_passing_reading = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Passing Reading"].mean()
overall_passing_spending = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Overall Passing"].mean()
^ i got some warnings when i tried to run this data, so per xpert's advice, i added "observed = True" to get rid of said warning.
size_bins = [0, 1000, 2000, 5000]
labels = ["Small (<1000)", "Medium (1000-2000)", "Large (2000-5000)"]
per_school_summary["School Size"] =
per_school_summary
size_math_scores = per_school_summary.groupby(["School Size"])["Average Math Score"].mean()
size_reading_scores = per_school_summary.groupby(["School Size"])["Average Reading Score"].mean()
size_passing_math = per_school_summary.groupby(["School Size"])["% Passing Math"].mean()
size_passing_reading = per_school_summary.groupby(["School Size"])["% Passing Reading"].mean()
size_overall_passing = per_school_summary.groupby(["School Size"])["% Overall Passing"].mean()
average_math_score_by_type = per_school_summary.groupby(["School Type"])["Average Math Score"].mean()
average_reading_score_by_type = per_school_summary.groupby(["School Type"])["Average Reading Score"].mean()
average_percent_passing_math_by_type = per_school_summary.groupby(["School Type"])["% Passing Math"].mean()
average_percent_passing_reading_by_type = per_school_summary.groupby(["School Type"])["% Passing Reading"].mean()
average_percent_overall_passing_by_type = per_school_summary.groupby(["School Type"])["% Overall Passing"].mean()


Xpert had me use lambda functions because there were issues with how my data was being read; it appeared that some of my numeric values were being stored as strings, so I was given these functions to get around it. 
district_summary_df["Total Students"] = district_summary_df["Total Students"].apply(lambda x: "{:,}".format(x))
district_summary_df["Total Budget"] = district_summary_df["Total Budget"].apply(lambda x: "${:,.2f}".format(x))
along with that, it also had me use another function to convert one of the data types so that my formatting would work, instead of giving me errors when i tried to run said code. district_summary_df["Total Budget"] = pd.to_numeric(district_summary_df["Total Budget"], errors='coerce')

per_school_counts = school_data.groupby("school_name")["size"].max() from xpert after asking how to find the numerical data sizes; I did the .max() function to see the school sizes because the count function didn't display the proper data. I also got the print idea from xpert as well.

passing_math_df = school_data_merge[school_data_merge["math_score"] >= 70]
passing_math_count_per_school = passing_math_df.groupby("school_name")["student_name"].count()
^ From xpert to be able to properly calculate passing count per school as i had trouble figuring out how to group the data

sorted_index = school_name["school_name"].sort_values()

per_school_summary.set_index(sorted_index, inplace=True)
^ Both functions above also from xpert.

This part was originally my code but it wasn't correct: top_schools = per_school_summary.sort(per_school_summary["% Overall Passing"])
Xpert helped me correct it to the following: top_schools = per_school_summary.sort_values(by = "% Overall Passing", ascending = False)

I learned how to use the cut function: 
pandas.cut(x, bins, right=True, labels=None, retbins=False, precision=3, include_lowest=False, duplicates='raise', ordered=True) from this link: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.cut.html

Other help from xpert:
df['column1'] = df['column1'].astype(float)
df['column2'] = df['column2'].astype(float)
index=labels
^ to put inside the code when creating the spending_summary dataframe
added ".mean()" to my function so that it would show actual results
analysis_text_part1 = """; xpert had me break apart my analysis text and use triple quotation marks when I had trouble printing my final analysis.

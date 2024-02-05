# CSS_streamlit
CSS Project - Option 2: Streamlit

# -*- coding: utf-8 -*-
"""
Created on Sun Feb  4 20:31:57 2024

@author: DELL
"""

import streamlit as st
import pandas as pd
import plotly.express as px

# Title with justified text and font size 36 using HTML
st.markdown("""
    <h1 style="text-align: justify; font-size: 36px;">The Effect of Carbon Nanotube (CNT) Concentration on Adhesive Strength of Canola Protein Bioadhesives</h1>
""", unsafe_allow_html=True)



# Header 1
st.header("Abstract")
text = """
This study includes incorporating pristine CNTs into the canola protein isolate (CPI) matrix. 
The incorporation of pristine CNT at 0.5% (w/w) loading was observed to be the optimum concentration (percentage loading where the highest adhesive strength was observed) after measuring the adhesive strengths in the range of 0.5-10% CNT concentration. 
At this CNT loading, the adhesive strength increased from 5.98 ± 0.27 MPa to 9.20 ± 0.64 MPa indicating an increase of 53.85% on dry adhesive strength basis; from 1.80 ± 0.71 MPa to 5.64 ± 0.88 MPa, denoting an increase of 213.33% on wet adhesive strength basis. 
Furthermore, at the aforementioned CNT’s loading, the adhesive strength increased from 5.42 ± 0.19 MPa to 7.44 ± 0.36 MPa, indicating an increase of 37.27% on a soaked adhesive strength basis.
"""

# Display the text with specified formatting
st.markdown(f"<div style='text-align: justify; font-size: 24px;'>{text}</div>", unsafe_allow_html=True)


# Bold thick line
st.markdown('<hr style="border-top: 3px solid black;">', unsafe_allow_html=True)

# Header 2
st.header("Research data")


# Data for the additional table
data_additional = {
    "States": ["Dry state", "Wet state", "Soaked state"],
    "Preparation": ["Dried for seven days at 25°C and 50% RH", "Immersed in tap water for two days", "Soaked in tap water for two days, then conditioned for an additional seven days at 25°C and 50% RH"],
    "Test": ["Shear strength break test", "Shear strength break test", "Shear strength break test"],
}

df_additional = pd.DataFrame(data_additional)

# Apply styles to the DataFrame
styled_df = df_additional.style \
    .set_table_styles([
        {"selector": "th", "props": [("font-size", "24px"), ("font-weight", "bold"), ("text-align", "center")]},  # Header font size, weight, and center alignment
        {"selector": "td", "props": [("font-size", "24px"), ("text-align", "justify")]}  # Data cell font size and justification
    ]) \
    .apply(lambda x: ['background-color: lightblue' if i in [0, 2] else 'background-color: thistle' for i in range(len(x))], axis=1)

text = """
Different states of the adhesive strengths were evaluated according to EN-204 durability tests.
"""

styled_text = f'<p style="font-size: 20px; text-align: justify; font-weight: bold;">{text}</p>'
st.markdown(styled_text, unsafe_allow_html=True)

# Convert the styled DataFrame to HTML and apply custom CSS for height
styled_html = styled_df.to_html(index=False)
styled_table = f'<style>div.stDataFrame > div.dataframe.table-container {{ max-height: 800px; overflow: auto; }}</style>{styled_html}'
st.markdown(styled_table, unsafe_allow_html=True)



# Bold thick line
st.markdown('<hr style="border-top: 3px solid black;">', unsafe_allow_html=True)
# Header 4
st.markdown("#### The dry adhesive state;")


import streamlit as st
import pandas as pd
import matplotlib.pyplot as plt

# Create sample data
data = {'% Concentration of CNT (w/w CPI)': [0, 0.5, 1, 3, 5, 7, 10],
        'Adhesive Strength (MPa)': [5.98, 9.20, 8.69, 8.17, 7.01, 5.25, 3.28],
        'Error Bar (MPa)': [0.28, 0.32, 0.41, 0.14, 0.29, 0.4, 0.22]}
df = pd.DataFrame(data)

# Set figure size
fig, ax = plt.subplots(figsize=(8, 6))


import streamlit as st
import pandas as pd

# Sample data
data = {
    "% Concentration of CNT": [0, 0.5, 1, 3, 5, 7, 10],
    "Adhesive Strength (MPa)": [5.98, 9.20, 8.69, 8.17, 7.01, 5.25, 3.28],
    "Error Bar": [0.28, 0.32, 0.41, 0.14, 0.29, 0.4, 0.22]
}

df = pd.DataFrame(data)

# Streamlit app
st.title("")

# Plotting the column chart
fig = px.bar(
    df,
    x="% Concentration of CNT",
    y="Adhesive Strength (MPa)",
    error_y="Error Bar",
    labels={"Adhesive Strength (MPa)": "Adhesive Strength", "% Concentration of CNT": "CNT Concentration"},
    title="The column bar showing the dry adhesive strengths of CPI at different CNT'S concentrations",
)

# Fixing dimensions on the x-axis
fig.update_xaxes(type='category')

# Customize tick labels to be bold
fig.update_layout(
    xaxis=dict(tickfont=dict(family='Arial, sans-serif', size=16, color='black')),
    yaxis=dict(tickfont=dict(family='Arial, sans-serif', size=16, color='black'))
)

# Display the chart
st.plotly_chart(fig)









# Bold thick line
st.markdown('<hr style="border-top: 3px solid black;">', unsafe_allow_html=True)
# Header 4
st.markdown("#### The wet adhesive state;")

import streamlit as st
import plotly.express as px
import pandas as pd

# Sample data
data = {
    "% Concentration of CNT": [0, 0.5, 1, 3, 5, 7, 10],
    "Adhesive Strength (MPa)": [1.80, 5.64, 4.69, 4.17, 2.01, 1.25, 1.28],
    "Error Bar": [0.28, 0.32, 0.41, 0.14, 0.29, 0.4, 0.22]
}

df = pd.DataFrame(data)

# Streamlit app
st.title("")

# Plotting the column chart
fig = px.bar(
    df,
    x="% Concentration of CNT",
    y="Adhesive Strength (MPa)",
    error_y="Error Bar",
    labels={"Adhesive Strength (MPa)": "Adhesive Strength", "% Concentration of CNT": "CNT Concentration"},
    title="The column bar showing the wet adhesive strengths of CPI at different CNT'S concentrations",
)

# Fixing dimensions on the x-axis
fig.update_xaxes(type='category')

# Custom CSS styling for bold, black, and larger text
css = """
    <style>
        .y-title, .x-title, .xticklabel, .yticklabel {
            font-family: Arial, sans-serif;
            font-size: 16px;
            color: black;
        }
    </style>
"""
st.markdown(css, unsafe_allow_html=True)

# Change the color of all columns to green
fig.update_traces(marker_color='green')

# Set the tickangle property to 0 for horizontal tick labels
fig.update_layout(xaxis=dict(tickangle=0))

# Display the chart
st.plotly_chart(fig)






# Bold thick line
st.markdown('<hr style="border-top: 3px solid black;">', unsafe_allow_html=True)
# Header 4
st.markdown("#### The soaked adhesive state;")

import streamlit as st
import plotly.express as px
import pandas as pd

# Sample data
data = {
    "% Concentration of CNT": [0, 0.5, 1, 3, 5, 7, 10],
    "Adhesive Strength (MPa)": [5.42, 7.44, 6.62, 6.44, 5.73, 4.01, 3.82],
    "Error Bar": [0.5, 0.34, 0.19, 0.29, 0.12, 0.27, 0.35]
}

df = pd.DataFrame(data)

# Streamlit app
st.title("")

# Plotting the column chart
fig = px.bar(
    df,
    x="% Concentration of CNT",
    y="Adhesive Strength (MPa)",
    error_y="Error Bar",
    labels={"Adhesive Strength (MPa)": "Adhesive Strength", "% Concentration of CNT": "CNT Concentration"},
    title="The column bar showing the soaked adhesive strengths of CPI at different CNT'S concentrations",
)

# Fixing dimensions on the x-axis
fig.update_xaxes(type='category')

# Change the color of all columns to pink
fig.update_traces(marker_color='darkred')

# Display the chart
st.plotly_chart(fig)


# Bold thick line
st.markdown('<hr style="border-top: 3px solid black;">', unsafe_allow_html=True)
# Header 2
st.header("Conclusion")

text = """
The results demonstrated that the incorporation of CNT at the optimal concentration can significantly enhance the adhesive properties of CPI. The insights from this research can pave the way for the development of high-performance bio-based adhesives for a range of applications, highlighting the importance of carefully selecting CNT concentrations in achieving the desired adhesive performance.
"""

# Streamlit app
st.title("")

# Display the text with specified formatting
st.markdown(f"<div style='text-align: justify; font-size: 24px;'>{text}</div>", unsafe_allow_html=True)



import streamlit as st

# Table of Contents
st.sidebar.title("Table of Contents")

# Sections
sections = ["Title", "Abstract", "Research Data", "Dry Adhesive State", "Wet Adhesive State", "Soaked Adhesive State", "Conclusion"]

# Display the sections as a list
for section in sections:
    if section in ["Abstract", "Dry Adhesive State", "Soaked Adhesive State"]:
        st.sidebar.write(f"- <span style='background-color: lightblue; font-size: 26px; font-weight: bold;'>{section}</span>", unsafe_allow_html=True)
    else:
        st.sidebar.write(f"- <span style='background-color: thistle; font-size: 26px; font-weight: bold;'>{section}</span>", unsafe_allow_html=True)

# Add a horizontal line to separate the table of contents from the main content
st.sidebar.markdown('<hr style="border-top: 2px solid #ccc;">', unsafe_allow_html=True)

# Main Content

# Your existing code goes here


































1. HTML Title
The code begins with an HTML title using the st.markdown function to display a formatted title with justified text and a font size of 36.

2. Abstract Section
The next section includes the abstract of the research. The st.header function is used to create a header, and the st.markdown function is employed to display text with specific formatting.

3. Additional Information Table
A table is created using a pandas DataFrame (df_additional) to display information related to different states of adhesive strengths. The table is styled with different background colors for better visibility. The table is then converted to HTML, and custom CSS is applied to control the height of the table. The final styled table is displayed using st.markdown.

4. Dry Adhesive State Plot
The dry adhesive state is visualized using a column bar chart created with Plotly Express. The data is provided as a DataFrame (df), and the chart is customized with labels, title, and styling. The chart is then displayed using st.plotly_chart.

5. Wet Adhesive State Plot
Similar to the dry state, the wet adhesive state is visualized using another column bar chart with customized styling and displayed with st.plotly_chart.

6. Soaked Adhesive State Plot
The soaked adhesive state is visualized using yet another column bar chart with custom styling and displayed using st.plotly_chart.

7. Conclusion Section
The conclusion section contains a formatted text discussing the results of the research. The st.markdown function is used to display the text.

8. Table of Contents Sidebar
The code includes a sidebar with a table of contents, listing various sections of the research. Different background colors are used for different sections. The st.sidebar functions are utilized to create the sidebar.

9. Horizontal Lines
Throughout the code, horizontal lines are used to separate different sections for better visual organization. These lines are created using the st.markdown function with HTML <hr> tags.

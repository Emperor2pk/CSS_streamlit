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

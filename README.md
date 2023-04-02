# 5_Peer_Graded_Assignment_Questions.py
Data Analysis with Python Final Project - US Domestic Airline Flights Interactive Dashboard

main things that i switched r how the imports are written 

# Import required libraries
import pandas as pd
import dash
import jupiter_dash 
from dash import dcc
from dash import html
from dash.dependencies import Input, Output, State
from jupyter_dash import JupyterDash
import plotly.graph_objects as go
import plotly.express as px
from dash import no_update

Tasks
# TASK1: Add title to the dashboard
html.H1(
    children="US Domestic Airline Flights Performance",
    style={'textAlign': 'center', 'color': '#503D36', 'fontSize': 24}
    ),
                    
# TASK2: Add a dropdown
dcc.Dropdown(id='input-type',
            options=[
                {'label': 'Yearly Airline Performance Report', 'value': 'OPT1'},
                {'label': 'Yearly Airline Delay Report', 'value': 'OPT2'}
                    ],
            placeholder='Select a report type',
            style={'width': '80%', 'padding': '3px', 'text-align-last': 'center'}
            )

# TASK3: Add a division with two empty divisions inside. See above division for example.
        html.Div([
            html.Div([], id='plot4'),
            html.Div([], id='plot5')
        ], style={'display': 'flex'}),
    ]
)

# TASK4: Add 5 ouput components

@app.callback([Output(component_id='plot1', component_property='children'),
 Output(component_id='plot2', component_property='children'),
 Output(component_id='plot3', component_property='children'),
 Output(component_id='plot4', component_property='children'),
 Output(component_id='plot5', component_property='children')],
               [Input(component_id='input-type', component_property='value'),
                Input(component_id='input-year', component_property='value')],
               # REVIEW4: Holding output state till user enters all the form information. In this case, it will be chart type and year
               [State("plot1", 'children'), State("plot2", "children"),
                State("plot3", "children"), State("plot4", "children"),
                State("plot5", "children")
               ])
               
# TASK5: Average flight time by reporting airline
line_fig = px.line(line_data, x='Month', y='AirTime', color='Reporting_Airline', title='Average monthly flight time (minutes) by airline')

# TASK6: Number of flights flying to each state from each reporting airline
tree_fig = px.treemap(tree_data, path=['DestState', 'Reporting_Airline'], 
          values='Flights',
          color='Flights',
          color_continuous_scale='RdBu',
          title='Flight count by airline to destination state')


# Run stuff
python3 -m pip install packaging
python3 -m pip install pandas dash
python3 5_Peer_Graded_Assignment_Questions.py

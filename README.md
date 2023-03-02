#                                                     Cryptocurrencies


OVERVIEW OF THE PROJECT(From the ASSESMENT)
  Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked you to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

SUMMARY 
  In here we are going to be processing data from pca while be clustering K-Mean, and wwill be reducing data dimensions using pca. we will be doing three plots first is the elbow curved,
  
# Create an elbow curve to find the best value for K.
inertia = []
k = list(range(1, 11))
# Calculate the inertia for the range of K values
for i in k:
   km = KMeans(n_clusters=i, random_state=0)
   km.fit(pcs_df)
   inertia.append(km.inertia_)

elbow_data = {"k":k,"inertia":inertia}
df_elbow = pd.DataFrame(elbow_data)
df_elbow.hvplot.line(x="k",y="inertia",xticks=k,title="Elbow Curve")

  <img width="840" alt="Screen Shot 2023-03-02 at 4 13 07 AM" src="https://user-images.githubusercontent.com/115046550/222384207-383bf5a8-3ccb-450d-85c3-b549cad5c228.png">

THEN IS THE 3D 
# Creating a 3D-Scatter with the PCA data and the clusters
fig = px.scatter_3d(
    clustered_df,
    x="PC1",
    y="PC2",
    z="PC3",
    hover_name="CoinName",
    hover_data=["Algorithm"],
    color="class",
    symbol="class",
    width=800,
)
fig.update_layout(legend=dict(x=0, y=1))
fig.show()

<img width="963" alt="Screen Shot 2023-03-02 at 4 14 55 AM" src="https://user-images.githubusercontent.com/115046550/222384674-f13a8b7b-3d43-49a5-b7bb-d676b1f60ef3.png">


THIRD IS HVPLOT.SCATTER PLOT

# Create a hvplot.scatter plot using x="TotalCoinsMined" and y="TotalCoinSupply".
# YOUR CODE HERE
plot_df.hvplot(
    kind="scatter",
    x="TotalCoinsMined",
    y="TotalCoinSupply",
    by="class",
    cmap="Magma",
    hover_cols=["CoinName"],
)

<img width="824" alt="Screen Shot 2023-03-02 at 4 16 42 AM" src="https://user-images.githubusercontent.com/115046550/222385107-5643ba6e-7f96-4589-9903-bab9ddd55d27.png">


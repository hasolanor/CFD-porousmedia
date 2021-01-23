# Appendix: Evaluation of the timestep independence regarding chemical scalar transport and retention problem

In order to select a proper timestep in the proposed CFD simulations, a previous evaluation of time step independence is carried out. Keeping this in mind, the proposed numerical experiment framework is run until 300 s for several timesteps. Then, the results are post-processed and a concentration profile over a horizontal axis (parallel to x-axis) is obtained for each considered timestep.

<table style="width:100%">
  <tr>
    <th>Steps</th>
    <th>Timestep (s)</th>
    <th>Mean Courant</th>
    <th>Max. Courant</th>
  </tr>
    <td>1</td>
    <td>300</td>
    <td>575.96</td>
    <td>6073.88</td>
  </tr>
  <tr>
    <td>10</td>
    <td>30</td>
    <td>57.596</td>
    <td>607.388</td>
  </tr>
  <tr>
    <td>30</td>
    <td>10</td>
    <td>19.1987</td>
    <td>202.463</td>
  </tr>
  <tr>
    <td>50</td>
    <td>6</td>
    <td>11.5192</td>
    <td>121.478</td>
  </tr>
  <tr>
    <td>300</td>
    <td>1</td>
    <td>1.91987</td>
    <td>20.2463</td>
  </tr>
</table>

<figure>
  <img src="./Figures/ScalarTranport/dtsensibility.png" alt="sensibility" style="width: 10px">
  <figcaption>Figure. Concentration profile over a horizontal axis at y=0.0007m.</figcaption>
</figure>

<figure>
  <img src="./Figures/ScalarTranport/dtsensibilityresiduals.png" alt="sensibility2" style="width: 10px">
  <figcaption>Figure. Concentration profile over a horizontal axis at y=0.0007m.</figcaption>
</figure>






# How to update a Pane when its activated
In the Pane class constructor add - 

this.Activated += myPane_Activated;

Then add this method -

private void myPane_Activated(object sender, EventArgs e)
{
    System.Diagnostics.Debug.WriteLine("Pane Activated");
}          

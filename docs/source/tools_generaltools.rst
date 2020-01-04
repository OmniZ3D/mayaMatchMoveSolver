General Tools
=============

The tools on this page are not specific to Markers, Cameras or
Bundles, but are general tools useful in Maya for many different
tasks.

Center 2D On Selection
----------------------

Forces the active viewport camera to lock it’s center to the currently
selected transform node.

A viewport camera can only center on one node at a time.

Usage (to *apply* centering effect):

1) Select transform node.

2) Activate a 3D viewport.

3) Run 'Apply 2D Center' tool.

   - The active viewport camera will be centered on the selected
     transform node.

4) Use the Pan/Zoom tool (default hotkey is '\' key), to zoom in and
   out. Play the Maya file and use the centered view as needed.

Usage (to *remove* centering effect):

1) Run 'Remove 2D Center' tool.

   - The active viewport will no longer center on an object, but will
     not reset the view.

   - The pan/zoom will still be active. To reset the viewport camera,
     turn off Pan/Zoom on the viewport camera (default hotkey is '\'
     key).

Run this Python command:

.. code:: python

    import mmSolver.tools.centertwodee.tool as tool

    # Apply Centering onto active camera
    tool.main()

    # Remove Centering from active camera
    tool.remove()

Smooth Keyframes
----------------

Smooth the selected keyframes in the Graph Editor. This tool also has
a UI to change the affect of the Smoothing function.

Usage:

1) Select keyframes in Graph Editor.

2) Run 'Smooth Selected Keyframes' tool.

3) Keyframe values will be smoothed.

Run this Python command:

.. code:: python

    import mmSolver.tools.smoothkeyframes.tool as tool

    # Smooth the selected Keyframes
    tool.smooth_selected_keyframes()

    # Open the Smooth Keyframes UI.
    tool.main()

Screen-Space Transform
----------------------

Convert a Maya transform node into a screen-space transform. This tool
will not modify the originally selected node, but will only create a
new node with new values.

When converting to Screen-Space the Screen Depth is calculated and the
transform node will still match the original transform in World-Space.

This tool may be used to convert an animated object into a
screen-space, then clean up or solve specific attributes, such as
screen X/Y or screen depth.

Usage:

1) Select transform nodes.

2) Activate viewport.

3) Run tool.

4) A new locator is created under the active camera

Run this Python command:

.. code:: python

    import mmSolver.tools.screenspacetransform.tool as tool
    tool.main()

Channel Sensitivity
-------------------

Channel sensitivity tool helps you to change the value of sensitivity
of channel slider setting. Using this tool the user to adjust
attributes in the Channel Box by very small increments, which is
useful for manually adjusting or matching parameters interactively.

Usage:

1) Run tool.

   - A UI will open, click the `Increase` or `Decrease` buttons to
     change the sensitivity.

2) Select an Attribute in the Channel Box.

3) Middle-mouse drag in the viewport to change the attribute value.

Run this Python command:

.. code:: python

    import mmSolver.tools.channelsen.tool as tool
    tool.main()

Copy Camera to Clipboard
------------------------

Saves the selected camera node into a temporary file and saves the
file path onto the OS Copy/Paste clipboard.

Usage:

1) Select a Maya camera.

2) Run tool.

3) Open 3DEqualizer

4) Select Camera in Object Browser.

5) Right-click and run "Paste Camera (MM Solver)...".

Run this Python command:

.. code:: python

    import mmSolver.tools.copypastecamera.tool as tool
    tool.main()

Marker Bundle Rename
--------------------

Renames selected markers and bundles connected, takes the input name
given in prompt window.

Usage:

1) Select Marker (or Bundle) nodes.

2) Run tool.

   - A prompt is displayed to enter the new name for the Marker and Bundles.

   - If the prompt is left at the default value ``marker``, then the
     Markers will named ``marker`` and Bundles will be named
     ``bundle``.

Run this Python command:

.. code:: python

    import mmSolver.tools.markerbundlerename.tool as tool
    tool.main()

Marker Bundle Rename (with Metadata)
------------------------------------

Renames the selected Markers and Bundles using only the metadata saved
onto the Marker nodes.

For example, metadata from 3DEqualizer is saved onto the Marker node.

Usage:

1) Select Marker (or Bundle) nodes.

2) Run tool.

   - Markers and Bundles are renamed based on metadata, if metadata is
     not found, the Marker/Bundle is not renamed.

Run this Python command:

.. code:: python

    import mmSolver.tools.markerbundlerenamewithmetadata.tool as tool
    tool.main()

Reparent Under Node
-------------------

This is equalivent to Maya's *Parent* tool (`p` hotkey), except the
tool will maintain the world-space position of the transform node for
each keyframe applied to the node.

Usage:

1) Select nodes to change parent, then select the new parent node.

   - The first nodes will become the children of the last selected node.

   - The last node is the new parent.

2) Run tool.

   - The first nodes are now parented under the last selected node,
     and will stay in the same position in world-space for all
     keyframes.

Run this Python command:

.. code:: python

    import mmSolver.tools.reparent.tool as tool
    tool.reparent_under_node()

Unparent to World
-----------------

This is equalivent to Maya's *Unparent* tool (`Shift + p` hotkey), except the tool will
maintain the world-space position of the transform node for each
keyframe applied to the node.

Usage:

1) Select Maya transform node(s).

   - The nodes may be in a deep hierarchy, or not.

2) Run tool.

   - The nodes will maintain the same world-space position, but will
     be unparented into root Maya Outliner (the nodes will not be
     parented under any node).

Run this Python command:

.. code:: python

    import mmSolver.tools.reparent.tool as tool
    tool.unparent_to_world()

Create / Remove Controller
--------------------------

Create a new transform node to control another node. The `Controller`
transform node can have a separate hierarchy than the source node.

Usage:

1) Select a Maya transform node.

2) Run 'Create Controller' tool.

   - A new 'Controller' locator node is created at the same position
     as the source transform.

3) Select and move the created Controller as you wish.

4) Select the Controller, run 'Remove Controller' tool.

   - The source node is baked at the same times as the Controller is
     keyed, and the Controller is deleted.

Run this Python command:

.. code:: python

    import mmSolver.tools.createcontroller.tool as tool

    # Create a Controller
    tool.create()

    # Remove selected Controller
    tool.remove()
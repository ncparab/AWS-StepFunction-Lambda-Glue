###############################################
AWS Step Function with AWS Lambda and AWS Glue
###############################################

AWS Step Functions is a web service that enables you to coordinate the components of distributed applications and microservices 
using visual workflows.

Step Functions offers a graphical console to visualize the components of your application as a series of steps. It automatically
triggers and tracks each step, and retries when there are errors, so your application executes in order and as expected, every 
time. Step Functions manages the operations and underlying infrastructure for you to ensure your application is available at 
any scale.

Steps to Create Step Function
------------------------------

Step 1 - Create a state machine.
+++++++++++++++++++++++++++++++++

- select ``Get Started`` from console.

.. image:: images/step1.png
   :width: 500px
   :height: 300px
   :alt: alternate text
   
- Define the state and click next 

.. image:: images/step2.png
   :width: 500px
   :height: 300px
   :alt: alternate text
   
Step 2 - Configure your state machine
++++++++++++++++++++++++++++++++++++++

- Create IAM role - Select role from IAM console

.. image:: images/step3.png
   :width: 500px
   :height: 300px
   :alt: alternate text
   
- Click on ``Create Role``

.. image:: images/step4.png
   :width: 500px
   :height: 300px
   :alt: alternate text
   
- Sletect ``Step Function`` as a AWS service and click on ``Next:Permission``

.. image:: images/step5.png
   :width: 500px
   :height: 300px
   :alt: alternate text

- Attach new created policies to step function. Click on ``Create Policy``.

.. image:: images/step7.png
   :width: 500px
   :height: 300px
   :alt: alternate text
   
- Review and Save the policy and click the ``Next:Tags``.

.. image:: images/step8.png
   :width: 500px
   :height: 300px
   :alt: alternate text

1) LambdaInvokePolicy

.. code-block:: json

   {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "lambda:CreateFunction",
                "lambda:InvokeFunction",
                "lambda:GetLayerVersion",
                "lambda:GetEventSourceMapping",
                "lambda:ListTags",
                "lambda:GetFunction",
                "lambda:GetAccountSettings",
                "lambda:GetFunctionConfiguration",
                "lambda:GetAlias",
                "lambda:GetLayerVersionPolicy",
                "lambda:GetPolicy"
            ],
            "Resource": "*"
          }
        ]
   }
     
2) GlueInvokePolicy

.. code-block:: json

   {
     "Version": "2012-10-17",
     "Statement": [
         {
             "Sid": "VisualEditor0",
             "Effect": "Allow",
             "Action": "glue:*",
             "Resource": "*"
          }
        ]
     }
     
- Attache the policies to role 

.. image:: images/step6.png
   :width: 500px
   :height: 300px
   :alt: alternate text

- review and name the role and create it.

.. image:: images/step10.png
   :width: 500px
   :height: 300px
   :alt: alternate text
   
- Configure the state machine with the created role as follows

.. image:: images/step11.png
   :width: 500px
   :height: 300px
   :alt: alternate text

- DashBoard is looks like this.

.. image:: images/step12.png
   :width: 500px
   :height: 300px
   :alt: alternate text


Step 3 - Start new execution as follow.
++++++++++++++++++++++++++++++++++++++++

- Click on state machine which you created and then click on ``Start Execution``

.. image:: images/step13.png
   :width: 500px
   :height: 300px
   :alt: alternate text

- See the flowchart of tasks mentioned in the step function


.. image:: images/step14.png
   :width: 500px
   :height: 300px
   :alt: alternate text
   
- once you start execution your connected lambda function and glue job started running


.. image:: images/step15.png
   :width: 500px
   :height: 300px
   :alt: alternate text

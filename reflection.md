# Reflection 

## Instructions :
Address:
* Which parts of the design do you feel most confident about, and which parts are you least sure about?
* At least one alternative architecture you considered and why you did not choose it.
* If you had 4–8 more weeks and unlimited credits, what next steps would you implement?

---

The part of the design that I am most confident in is the selected data sources: labs, symptoms, vitals, meds, and timestamps. They provide an accurate representation of the clinical requirements of hyperthyroidism monitoring, providing significant trend analysis. I am least confident in the analytics component, especially the clinical interpretation of trends and thresholds. Even though the system can recognize trends like suppressed TSH or rising T4 levels, more clinical validation and domain knowledge would be needed to identify acceptable thresholds for alerts or predictive indicators. Furthermore, even while the architecture supports automation and scalability, adding more analytics or real-time processing would add complexity that is beyond the scope of this project. Additional testing would be necessary to guarantee that analytics results are both technically correct and clinically significant.

One alternative architecture considered for this project was a fully serverless design using only Cloud Functions instead of Cloud Run containers. In this approach, file uploads to Cloud Storage would automatically trigger Cloud Functions for validation, processing, and database loading. With this design, we can reduce infrastructure management overhead.

With an additional 4 to 8 weeks and unlimited cloud credits, the next steps would focus on expanding both functionality and realism. Integrating standardized healthcare data formats like FHIR-based lab resources, instead of depending only on CSV uploads, would be a significant improvement. Additionally, I would put in place role-specific dashboards with more restrictive controls so that patients could only see their personal data and providers could see trends at the population level. From an analytics standpoint, I would go into more sophisticated trend detection or predictive modeling to find individuals who are more likely to experience issues like thyroid storm or atrial fibrillation. Lastly, in order to make the system more efficient and clinically significant, I would incorporate automated warnings and notifications, such as email or in-app messages, to inform providers when abnormal trends are found.

Overall, this project improved my comprehension of how cloud-based architectures might aid in monitoring chronic illnesses in the medical field. It illustrated how clinical context, data governance issues, and technical design choices work together to create a sustainable and scalable solution.

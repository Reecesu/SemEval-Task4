# Human Value Detection 2023
*SemEval 2023 Task 4. ValueEval: Identification of Human Values behind Arguments*

Task Description: Given a textual argument and a human value category, classify whether or not the argument draws on that category.

This task uses a set of 20 value categories compiled from the social science literature and described in our ACL paper. Participants can submit runs (also known as approaches or systems) that detect one, a subset, or all of these values in arguments. Arguments are given as premise text, conclusion text, and binary stance of the premise to the conclusion ("in favor of" or "against").


The 20 value categories are shown here on Schwartz' value continuum (click to see description):

| Value Categories:          |                               |                                  |
|----------------------------|-------------------------------|----------------------------------|
| 1. Self-direction: thought | 8. Face                       | 15. Benevolence: caring          |
| 2. Self-direction: action  | 9. Security: personal         | 16. Benevolence: dependability   |
| 3. Stimulation             | 10. Security: societal        | 17. Universalism: concern        |
| 4. Hedonism                | 11. Tradition                 | 18. Universalism: nature         |
| 5. Achievement             | 12. Conformity: rules         | 19. Universalism: tolerance      |
| 6. Power: dominance        | 13. Conformity: interpersonal | 20. Universalism: objectivity    |
| 7. Power: resources        | 14. Humility                  |                                  |

It is good to have own ideas and interests.
Contained values and associated arguments (examples):


- **Be creative:** arguments towards more creativity or imagination
- **Be curious:** arguments towards more curiosity, discoveries, or general interestingness
- **Have freedom of thought:** arguments toward people figuring things out on their own, towards less censorship, or towards less influence on thoughts


Data is provided as tab-separated values files with one header line. We will provide an extended training set, a validation set, and the test set (the latter without labels) end of November 2022. Stay up-to-date and report problems on the task mailing list. [download]
The arguments-training/validation/testing.tsv files contain one argument per line: its unique argument ID, the conclusion, the premise's stance towards the conclusion, and the premise itself. Example with tab-separated columns highlighted (click link):
The labels-training/validation/testing.tsv files also contain one argument per line: its unique argument ID and one column for each of the 20 value categories with a 1 meaning that the argument resorts to the value category and a 0 that not. Example with tab-separated columns highlighted:
 
#### Evaluation
>Runs are evaluated on the basis of F1-score, Precision, and Recall: averaged over all value categories and for each category individually. The runs are ranked according to the averaged F1-score.


#### Submission
>This task uses TIRA for submissions, which allows for both run file upload and Docker image submission. The latter allows for excellent reproducibility of your run. Registered teams will receive links to register with TIRA up to one work day after registration.
>For each topic and stance, include 10 retrieved images. Each registered team can submit up to 4 different runs. Teams are allowed to submit one additional "early bird" run on the final data until December 16. The submission format is the same as the labels-training/validation/testing.tsv with value category columns being optional (skip categories for which the run contains no prediction).
>To submit a run file, go to this task's TIRA page. Log in. Click "SUBMIT". Make sure "UPLOAD SUBMISSION" is selected. Specify your file and the dataset and "UPLOAD".
>To submit a Docker image, go to this task's TIRA page. Log in. Click "SUBMIT". Make sure "DOCKER SUBMISSION" is selected. Click on "UPLOAD IMAGES" and follow the instructions. Once uploaded, click on "ADD CONTAINER". Specify the command and the Docker image and "ADD CONTAINER". A randomly named tab is created. Click on it, specify the dataset and "RUN CONTAINER". You can copy the random baseline to get started with Docker submissions.
>In case of problems or questions concerning TIRA, please use the TIRA forum. Note: At the moment, the TIRA web interface sometimes fails to provide feedback on actions. Reload the page in such cases.




# Touché23-Human-Value-Detection
DOI: https://doi.org/10.5281/zenodo.6814563
Version: 2022-07-11

Dataset for [Touché / SemEval 2023 Task 4; ValueEval: Identification of Human Values behind Arguments](https://touche.webis.de/semeval23/touche23-web). Based on the original [Webis-ArgValues-22 dataset](https://doi.org/10.5281/zenodo.5657249) accompanying the paper [Identifying the Human Values behind Arguments](https://webis.de/publications.html#kiesel_2022b), published at ACL'22.

The dataset currently contains 5220 arguments. We are, however, looking for more argument datasets (conclusion + stance + premise) to annotate and incorporate, especially datasets from different cultures and genres. Please send suggestions to our [task](mailto:valueeval@googlegroups.com) or [organizers](mailto:valueeval-organizers@googlegroups.com) mailing lists.




## Argument Corpus
The annotated corpus in tab-separated value format. Future versions of this dataset will contain more arguments and be split into "-training", "-validation", and "-testing" files to represent the corresponding sets for the evaluation.
- `arguments-training.tsv`: Each row corresponds to one argument
    - `Argument ID`: The unique identifier for the argument
    - `Conclusion`: Conclusion text of the argument
    - `Stance`: Stance of the `Premise` towards the `Conclusion`; one of "in favor of", "against"
    - `Premise`: Premise text of the argument
- `labels-training.tsv`: Each row corresponds to one argument
    - `Argument ID`: The unique identifier for the argument
    - Other: Each other column corresponds to one value category, with a 1 meaning that the argument resorts to the value category and a 0 that not
- `level1-labels-training.tsv`: The same as `labels-training.tsv` but for the 54 level 1 values of the taxonomy (used in human annotation). Though not used for the 2023 task (except for the annotation), participants can still use them in their approaches.


## Value Taxonomy
The `value-categories.json` describes the 20 value categories of this task through examples. Format:
```
{
  "<value category>": {
    "<level 1 value>": [
      "<exemplary effect a corresponding argument might target>",
      ...
    ], ...
  }, ...
}
```
The level 1 values are not used for the 2023 task (except for the annotation), but are still listed here for some might find them useful for understanding the value categories. See our paper on [Identifying the Human Values behind Arguments](https://webis.de/publications.html#kiesel_2022b) for the complete taxonomy.


## Authors
- Johannes Kiesel, Bauhaus-Universität Weimar, johannes.kiesel@uni-weimar.de
- Milad Alshomary, Paderborn University, milad.alshomary@upb.de
- Nicolas Handke, Universität Leipzig, nh54fapa@studserv.uni-leipzig.de
- Xiaoni Cai, Technische Universität München, caix@in.tum.de
- Henning Wachsmuth, Paderborn University, henningw@upb.de
- Benno Stein, Bauhaus-Universität Weimar, benno.stein@uni-weimar.de


## Version History
- 2022-07-11
  - Exchanged the values.json from original dataset with task-specific value-categories.json

- 2022-07-09
  - Initial


## License
This dataset is distributed under [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/).


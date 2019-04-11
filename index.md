---
layout: default
---

# About Me

I'm a master's student at Johns Hopkins with research interests in computer vision and machine learning with medical applications. I'm currently working with [Ayushi Sinha](https://www.cs.jhu.edu/~ayushis/).

# Projects

* [Unsupervised Tool Detection in Endoscopic Video Frames](github.com/zdavidli/tool-presence)
    * Can we use a variational autoencoder to learn tool representation in surgical video and start to provide labels to medical data?
* [Chirp](github.com/zdavidli/chirp)
    * A Twitter bot that reads tweets in the voice of the tweeter. Voice model is trained using one-shot learning. 
* [Longitudinal In-vivo Detection of Synapses](github.com/zdavidli/LIDS)
    * Track and detect synapses in live mice as they learn motor tasks. Brain scans are taken via two-photon microscopy.
* [Neural Style Removal](github.com/zdavidli/neural-style-removal)
    * Can we improve object detection in abstract artwork by first applying neural style transfer to make artwork more realistic?
    * [Project Report](assets/object-detection-artwork.pdf)
* [RNN Stock Prediction](github.com/zdavidli/rnn-stock-prediction)
    * Can we beat the market by using an RNN trained on intraday stock data to predict stock market trends?
    * [Project Report](assets/rnn-stock-prediction.pdf)

# Teaching

I've helped teach a few classes while here at JHU and I've uploaded a collection of notes I made for teaching

* [Calculus III](calc3.html)


# Posts
<ul>
    {% for post in site.posts %}
        <li>
            <a href="{{ post.url }}">
            {{ post.title }}
            </a>
            - <time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time>
        </li>
    {% endfor %}
</ul>
